## 마이크로서비스 API 활용사례 3. 통합대기환경정보 제공



이 장에서는 마이크로서비스 아키텍처 기반 통합대기환경정보 개발 사례를 소개한다. 통합대기환경 정보는 초미세먼지 현황 및 대기환경 정보를 한국환경공단에서 제공하는 OPEN API를 기반으로 개발한 사례이다. 일반적인 개발의 경우 API를 공공데이터포털이나 한국환경공단 제공 API를 호출하여 서비스를 개발할 수도 있지만 마이크로서비스 스튜디오를 활용하여 개발하는 방법과 실제 개발한 사례를 소개한다.



### 통합대기환경정보 API ?

#### 1. 기본 기능

| 주요 기능      | 기능 설명                                                    | 기타(비고)                                                   |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 행정구역지도   | 국토지리정보에서 제공하는 행정구역이 표시된 지도 파일을 이용하여 행정구역별 정보 제공 | 행정구역 지도 제공처 : GIS개발자 사이트, 주소정보제공 시스템 등<br />- SHP 파일로 제공됨 |
| 실시간미세먼지 | 실시간 초미세먼지 및 미세먼지 등 대기환경 정보 제공          | 한국환경공단 정보 이용<br />실시간 초미세먼지 정보 API 호출  |
| 대기환경정보   | 실시간 통합대기환경 정보 제공                                | - 한국환경공단 정보 이용<br />- 실시간 통합대기환경정보 API 호출 |



#### 2. 상세 기능 설명

1) 행정구역 지도 : 행정구역 표시 지도를 웹사이트에서 제공함. SHP 최신화

2) 실시간 초미세먼지 및 미세먼지 정보 : 행정구역별 초미세먼지 현황을 환경오염 농도별 색상으로 표시해줌

3) 실시간 통합대기환경 : 행정구역별 상세 지역별 통합 대기환경정보 제공, 일산화탄소 등 그래프로 농도 표시

4) 대기환경 점수를 지소로 환산한 정보 제공, 지수값을 그래프로 제공



### 단위 애플리케이션 분할 방법

행정구역별 실시간 통합대기환경 정보 제공을 위한 초미세먼지와 통합대기환경 정보를 나눌 수 있다.

|                    서비스 단위별 분할                    |                       기능별 분할                        |
| :------------------------------------------------------: | :------------------------------------------------------: |
| <img src="./images/msa3_fd01.png" width=400 height=300 > | <img src="./images/msa3_fd02.png" width=320 height=300 > |



### 마이크로서비스 애플리케이션 설계

#### 1. 서비스 정의

마이크로서비스 단위의 분할이 확정되면, 서비스와 서비스간의 통신 방법(규약)을 정하고 FRONTEND와 BACKEND로 구분한다. 서비스간의 통신 규약은 여러가지가 있으나 여기에서는 REST API 방식을 사용한다. 

<img src="./images/msa1_apt04.png" width=350 height=230 >



#### 2. API 설계

초미세먼지 및 통합대기환경 정보를 이용하여 유용한 API를 도출하여 아래와 같이 정의한다.

| URL                                                 | Method | Parameters  |        | Return | Status  |
| --------------------------------------------------- | ------ | ----------- | ------ | ------ | ------- |
| /api/dust/measure/list?sidoName=&pageNo=&numOfRows= | GET    | sidoName    | String | LIST   | 200(OK) |
|                                                     |        | pageNo      | long   | LIST   | 200(OK) |
|                                                     |        | numOfRows   | long   | LIST   | 200(OK) |
| /api/dust/measure/list/all?sidoName=                | GET    | sidoName    | String | LIST   | 200(OK) |
| /api/dust/cai/list?sidoName=&pageNo=&numOfRows=     | GET    | sidoName    | String | LIST   | 200(OK) |
|                                                     |        | pageNo      | long   | LIST   | 200(OK) |
|                                                     |        | numOfRows   | long   | LIST   | 200(OK) |
| /api/dust/cai/list/all?sidoName=                    | GET    | sidoName    | String | LIST   | 200(OK) |
| /api/dust/cai?pollutant=&stationName=               | GET    | pollutant   | String | Object | 200(OK) |
|                                                     | GET    | stationName | String | Object | 200(OK) |
| /api/dust/measure/avg/sido?pollutant=               | GET    | pollutant   | String | Object | 200(OK) |
| /api/dust/measure/avg/time/sigungu?sidoName=&hour=  | GET    | sidoName    | String | LIST   | 200(OK) |
|                                                     | GET    | hour        | String | LIST   | 200(OK) |
| /api/dust/measure/avg/sigungu?sidoName=             | GET    | sidoName    | String | LIST   | 200(OK) |

**Parameters 정보**

| 출력변수명  | Type   | 예제   | 설명               |
| ----------- | ------ | ------ | ------------------ |
| sidoName    | String | 서울   | 조회할 도 이름     |
| stationName | String | 강남구 | 조회할 측정소명    |
| pageNo      | Long   | 2      | 조회할 페이지 번호 |
| numOfRows   | Long   | 20     | 조회할 데이터의 양 |
| hour        | String | 15:00  | 조회할 시간        |
| pollutant   | String | pm10   | 오염물질 명        |



**미세먼지 API 조회 출력 결과**

| 출력 변수명 | Type   | 설명                                   |
| :---------: | ------ | -------------------------------------- |
| stationName | String | 측정장소 이름                          |
|  cityName   | String | 시군구 이름                            |
|  dataTime   | String | 날짜                                   |
|  so2Value   | String | 아황산가스 측정 농도                   |
|   coValue   | String | 일산화탄소 측정 농도                   |
|  no2Value   | String | 오존 측정 농도                         |
|   o3Value   | String | 이산화질소 측정 농도                   |
|  pm10Value  | String | 미세먼지(pm10) 측정농도                |
|  pm25Value  | String | 초미세먼지(pm25) 측정농도              |
| pm10Value24 | String | 미세먼지(pm10) 24시간 예측 평균 농도   |
| pm25Value24 | String | 초미세먼지(pm26) 24시간 예측 평균 농도 |
|    ovSo2    | String | 아황산가스 지수값                      |
|    cvCo     | String | 일산화탄소 지수값                      |
|    cvNo2    | String | 오존 지수값                            |
|    cvO3     | String | 이산화질소 지수값                      |
|   cvPm10    | String | 미세먼지(pm10) 지수값                  |
|   cvPm25    | String | 초미세먼지(pm25) 지수값                |
|  khaiValue  | String | 통합대기환경지수                       |
|   grades    | List   | 오염물질 별 등급 리스트                |
|    name     | String | 오염물질 명                            |

| 출력변수명 | Type   | 설명                  |
| ---------- | ------ | --------------------- |
| value      | String | 통합대기환경지수      |
| grade      | String | 통합대기환경지수 등급 |
| seoul      | String | 오염물질 서울 평균    |
| busan      | String | 오염물질 부산 평균    |
| daegu      | String | 오염물질 대구 평균    |
| incheon    | String | 오염물질 인천 평균    |
| gwangju    | String | 오염물질 광주 평균    |
| daejeon    | String | 오염물질 대전 평균    |
| ulsan      | String | 오염물질 울산 평균    |
| gyeonggi   | String | 오염물질 경기 평균    |
| gangwon    | String | 오염물질 강원 평균    |
| chungbuk   | String | 오염물질 충북 평균    |
| chungnam   | String | 오염물질 충남 평균    |
| jeonbuk    | String | 오염물질 전북 평균    |
| jeonnam    | String | 오염물질 전남 평균    |
| gyeongbuk  | String | 오염물질 경북 평균    |
| gyeongnam  | String | 오염물질 경남 평균    |
| jeju       | String | 오염물질 제주 평균    |
| sejong     | String | 오염물질 세종 평균    |



#### 3. API 호출 방법

BACKEND에 정의한 API에서 호출하여 결과값을 보여줌

<img src="./images/msa3_fd03.png" width=700 height=300 >



##### API 호출 

```
@RestController
@RefreshScope
@RequestMapping(value="/api/dust")
public class DustMeasureController 
{
	@Autowired
	DustMeasureService dustMeasureService;
	@ApiOperation("해당 도의 미세먼지 실시간 측정 데이터 조회 API - 페이징")
    @RequestMapping(value="/measure/list", method = RequestMethod.GET)
    @ResponseStatus(HttpStatus.OK)
 }

```



각각 단일 서비스로 개발하고 REST API를 이용하여 다른 서비스 적용

<img src="./images/msa3_fd04.png" width=700 height=400 >



### 통합대기환경 정보 제공 개발 결과 확인

현재 샘플로 만들어진 사이트가 공개되어 있습니다.

- 접속 사이트 URL : http://fine-dust-map-fd-service.k-cloud.org

본 개발 결과는 Github에 소스코드가 공개되어 있습니다.

- Github 공개 소스코드 : https://github.com/startupcloudplatform/fine-dust
