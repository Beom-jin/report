# terminal 이름 
# 위키피디아에서 가져옴
# URL:https://ko.wikipedia.org/wiki/%EB%B6%84%EB%A5%98:%EB%8C%80%ED%95%9C%EB%AF%BC%EA%B5%AD%EC%9D%98_%EB%B2%84%EC%8A%A4_%ED%84%B0%EB%AF%B8%EB%84%90
## 라이브러리 설치
```
pip install selenium
```
```
pip install bs4
```
```
pip install pandas
```

## 라이브러리 로드
```
from selenium import webdriver
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.common.by import By
from bs4 import BeautifulSoup
from urllib.request import urlopen
import requests
import pandas as pd
```

## 데이터 로드
### 알집파일 경로 추가하면 됩니다.
```
data=pd.read_excel('C:\\Users\\qjawl\\Desktop\\빅데이터\\빅데이터프로젝트\\UAM\\20210828\\다시구한데이터\\터미널.xlsx')
```
## for 문에서 사용하기 위해 array로 만들어줌 
```
import numpy as np
data=np.array(data)
```

## 카카오 API 이용 -> Rest KEY 부분 자신 고유 카카오 APi 인증 키 입력
```
import requests 
from urllib.parse import urlparse
data_result=[]

for add in data:
    for address in add:
        url = "https://dapi.kakao.com/v2/local/search/keyword.json?"+'query='+address
        result = requests.get(urlparse(url).geturl(),headers={"Authorization":"Rest Key"})
        json_obj = result.json()
        print(json_obj)
        for document in json_obj['documents']:
            val = [document['x'],document['y']]
            data_result.append(val)
df = pd.DataFrame(data_result, columns = ['LAT','LON'])
```

## 결과 데이터 프레임으로 변환 후 저장
```
coord=pd.DataFrame(coord)
coord.to_excel('C:\\Users\\qjawl\\Desktop\\빅데이터\\빅데이터프로젝트\\UAM\\20210828\\터미널다시\\터미널.xlsx')
```
