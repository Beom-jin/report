# 비행 불가능 여부 크롤링
## 라이브러리 다운로드
```
pip install selenium
```
```
pip install bs4
```
```
pip install pandas
```
```
pip install numpy
```
## 라이브러리 로드
```
from selenium import webdriver
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.common.by import By
from bs4 import BeautifulSoup
from urllib.request import urlopen
from selenium.webdriver.common.keys import Keys
from xml.etree import ElementTree
import requests
import time
import pandas as pd
import numpy as np
```

## 데이터 로드 압축 파일 중 FOR_GONG이라는 데이터의 경로를 설정한다.
```
data=pd.read_csv('C:\\Users\\qjawl\\Desktop\\빅데이터\\빅데이터프로젝트\\UAM\\20210828\\for_gong.csv',encoding='EUC-KR')
```

## 로드한 데이터 중 주소만 가져오기
```
data_for_c=data.loc[:,['도로명']]
data_for_c=np.array(data_for_c)
data_for_c
```
