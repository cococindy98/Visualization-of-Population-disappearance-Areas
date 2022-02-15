![image](https://user-images.githubusercontent.com/83954540/154046984-dabc0fbd-84af-4da5-b86d-b3e03f4c593a.png)
---
## Introduction 
- 인구 소멸 위기 지역을 파악하고, 지도 위에 시각화를 수행합니다.
- 사용기술 : python pandas, numpy, seaborn, matplotlib, folium
---
## Contents
- [1. 프로젝트 소개](#1-프로젝트-소개)
  * [배경](#배경)
  * [프로젝트 개요](#프로젝트-개요)
- [2. 데이터 전처리](#2-데이터-전처리)
- [3. 데이터 시각화](#3-데이터-시각화)
---

## 1. 프로젝트 소개
### 배경 
- *인구 소멸 위기 지역 이란?*
> ‘한국의 ‘지방소멸’에 관한 7가지 분석’ 보고서를 쓴 이상호 한국고용정보원 부연구위원의 분석방법을 이용. 65세 이상 노인 인구와 20~39세 여성인구를 비교해 젊은 여성 >인구가 노인 인구의 절반에 미달할 경우 ‘인구소멸 위험 지역’으로 분류하는 방식이다.
- 인구가 특정 지역에만 밀집되어 있어, 몇몇 지자체가 사라질 위기에 처해있다는 [기사](https://www.joongang.co.kr/article/21902650#home)를 보았습니다.
- 인구 밀집 사태를 시각화로 제시하여 사태의 심각성을 표현하고자 합니다.
### 프로젝트 개요 
1. 프로젝트명 : 인구 소멸 지역 시각화
2. 수행자 : 이서영
3. 수행기간 : 2021.10월 중 하루 (토이 프로젝트)
4. 목표 : 카토그램으로 인구 소멸 지역을 시각화
5. 데이터 셋 : 공공데이터 활용(통계청), Lucky Park github

|데이터명|상세내용|
|:------:|:---:|
|Population|행정구역(읍면동)별/5세별 주민등록인구|
|south korea-maps| folium 시각화를 위한 시도별 경계선이있는 json 파일|
|draw_korea_raw|엑셀로 그린 대한민국 지도 파일 |
---
## 2. 데이터 전처리 
- 데이터를 위의 연령 정의에 맞는 범주로 전처리 해주었습니다.
- 분석에 필요한 컬럼만을 선택하여 pivot_table로 변환해주었습니다.
- 인구 소멸 비율을 정의에 따라 계산해 주었습니다.
- 추후 시각화를 위해 멀티인덱스와 멀티컬럼을 해제해주었습니다.
![image](https://user-images.githubusercontent.com/83954540/154051200-bbcab6e3-d135-40b1-8ca0-1d71d6ae8de6.png)

<br>

### 지도 시각화를 위한 지역별 ID만들기 
- 만들고자 하는 ID형태 : 서울 중구, 통영, 고양 덕양, 남양주, 인천 남동 ...
- 일반 시 이름과 세종시, 광역시도 일반 구 정리 

![image](https://user-images.githubusercontent.com/83954540/154051694-196464c4-160b-45bf-a2b6-b19fe8088340.png)

- 행정구 정리
 
![image](https://user-images.githubusercontent.com/83954540/154051754-e4a93935-6a3a-425d-bb12-6542eda68d61.png)

---
## 3. 데이터 시각화 
- 시각화에 사용하는 함수는 다음 [혜식님의 깃헙](https://github.com/hyeshik?tab=repositories)을 참고하였습니다. 
- 카토그램으로 시각화를 위해 엑셀로 대한민국 지도를 그린 파일을 불러왔습니다.
- stack()을 활용해 지도그림의 좌표를 확보하였습니다.
- 지도의 경계선 좌표는 직접 작성하였습니다.
![image](https://user-images.githubusercontent.com/83954540/154051862-ce20aa85-ab11-4204-b323-7b8f6b1bb49d.png)

**인구 소멸 위기 지역 시각화 : 카토그램**
- 기사에서 제시한 30년 내 사라질 가능성이 높은 지자체 Top10과 비슷한 양상을 보임을 왼쪽 지도를 통해 확인할 수 있습니다
![image](https://user-images.githubusercontent.com/83954540/154052146-098c86a7-0795-4b8a-be37-7f65399cf670.png)

**인구 수 합계 시각화 : 카토그램**
- 대체적으로 수도권 지역에 인구가 밀집해있는 모습을 오른쪽 지도를 통해 확인할 수 있습니다. 
- 광역시, 자치시를 제외하면 외곽지역으로 갈수록 인구수가 적어지는 것을 볼 수 있습니다.
![image](https://user-images.githubusercontent.com/83954540/154052267-f95234f7-a6da-44fc-97ea-4e0c5c713490.png)

**2030여성 비율 시각화 : 카토그램**
- 수도권과 광역시에는 2030 여성의 비율이 적지 않음을 확인할 수 있습니다. 
- 다른 지역보다 강원도 상부 지역의 문제가 심각한것이 눈에 띕니다.

![image](https://user-images.githubusercontent.com/83954540/154053679-bfb7e8ec-8891-4de2-8dac-88f2a00d74ac.png)


**인구 소멸 위기 지역 시각화 : Folium**

![image](https://user-images.githubusercontent.com/83954540/154052508-1b732af6-7e04-4a4a-9ab1-c1822cd4ae2e.png)
