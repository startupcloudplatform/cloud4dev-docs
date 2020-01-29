# 백엔드앱 개발

 

## 오픈데이터API 게이트웨이 시스템

### 오픈데이터 API 게이트웨이 포털 사용 방법 

1)     메인 페이지

​    ![1558421260238](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/opendataapi.png)  

\-       1. 로그인 및 회원가입

\-       2. 검색창

\-       3. 전체메뉴

\-       4. 메인 메뉴

\-       5. 카테고리

\-       6. 오픈데이터

\-       7. 인기 오픈데이터

\-       8. 공지사항 및 커뮤니케이션

\-       9. 관련 사이트 배너

 

2)     로그인

   ![1558421452765](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/openlogin.png) 



\-       1. ID 입력창

\-       2. Password 입력창 

3)     파일데이터 검색(상가(상권)정보)                        



\-       1. 파일데이터 검색창

\-       2. 파일데이터 검색 결과 

4)     상가(상권)정보 상세 정보

![1558422183096](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/bookmark.png)

\-       1. 상가(상권)정보 세부 정보

\-       2. 상가(상권)정보 파일

\-       3. 즐겨찾기 추가, 취소

\-       4. 다운로드 파일

 

5)     다운로드 파일 화면 

​        ![1558422323245](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/download.png)           

\-       1. 다운로드 파일 화면

\-       2. 다운로드 파일

 

6)     오픈데이터 API 검색(지정 상권조회)

​       ![1558572796563](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/searchopenapi.png)                  

\-       1. 오픈데이터 검색 창

\-       2. 오픈데이터 검색 결과



7)     지정 상권조회 API 상세 정보

​     ![1558572943817](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/storeapi.png)                     



\-       1. 지정 상권조회 API 상세 정보

\-       2. 즐겨찾기 추가, 데이터 신청, 취소






8)     지정 상권조회 예제 코드 조회

​      ![1558573046560](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/readcode.png)                                      



\-       1. 사용자 인증키

\-       2. 사용자 오픈 API

\-       3. 지정상권조회 예제 코드




### 상권 API 호출 방법

1)     지정 상권조회 코드 입력 화면

​     ![1558573133977](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/storecode.png)                                                         

\-       1. 예제로 제공된 코드를 개발자가 필요한 부분에 입력 및 파싱한 화면

 

2)     API 실행 결과 화면

![1558573244893](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/runapi.png)

   \-       1. 개발자가 입력 및 파싱 수행 한 결과 화면

 




## 빅데이터, AI 기반 상권분석 브로커

### 샘플앱 빅데이터/AI 서비스 브로커 상세 

| **URL**               | **파라미터**                                                 | **설명**                                                     |
| --------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| /collect/rest         | String apikey - 발급받은 apikey    String url - 수집할 REST api url    String method(선택) - http method(get/post)    String header(선택) - http header    String parameter(선택) - parameter    String path – 저장경로 | - 수집   서비스 브로커(Rest API 어댑터)   - rest api 를 통해 다운받은 데이터를 지정경로에 저장한다 |
| /save/appendrdb       | String apikey - 발급받은 apikey    String dbtype - db 종류(mysql/oracle/cubrid/mssql)    String dbserver - db server    Integer dbport - db port    String database - db database명    String uid - db 접속 계정    String pwd - db 접속 비밀번호    String table - db table 명    String data - 추가데이터(json 형식) | - 저장   서비스 브로커(DB 어댑터)   - 지정된 db 접속 정보를 이용하여 data object의 내용을 table 에 추가한다 |
| /save/updaterdb       | String apikey - 발급받은 apikey    String dbtype - db 종류(mysql/oracle/cubrid/mssql)    String dbserver - db server    Integer dbport - db port    String database - db database명    String uid - db 접속 계정    String pwd - db 접속 비밀번호    String table - db table 명    String data - 추가데이터(json 형식) | - 저장   서비스 브로커(DB 어댑터)   - 지정된 db 접속 정보를 이용하여 data object의 내용을 table 에 업데이트한다 |
| /save/deleterdb       | String apikey - 발급받은 apikey    String dbtype - db 종류(mysql/oracle/cubrid/mssql)    String dbserver - db server    Integer dbport - db port    String database - db database명    String uid - db 접속 계정    String pwd - db 접속 비밀번호    String table - db table 명    String data - 추가데이터(json 형식) | - 저장   서비스 브로커(DB 어댑터)   - 지정된 db 접속 정보를 이용하여 data object의 조건 에 맞는 데이터를 삭제한다 |
| /processing/etl       | String apikey - 발급받은 apikey    String inputcsvfile    String method    String ruletext    String sort    String sortindex    String outputcsv | - 가공   서비스 브로커(ETL 어댑터)   - 데이터 추출, 변환, 로드한다 |
| /analysis/{algorithm} | String apikey - 발급받은 apikey    String algorithm - 알고리즘명    Map<String, Object> parameters - 알고리즘 파라미터 | - 분석   서비스 브로커(분류 어댑터)   - 분석 기능 목록 에서 {algorithm}을 실행한다 |
| /ai/dong              | String apikey - 발급받은 apikey    String sido - 시도        | - AI 브로커(지능형 창업 후보지역 상권분석 어댑터)   - 선택한 지역의 동별 상권 정보를 가져온다 |
| /ai/sangho            | String apikey - 발급받은 apikey    String dong - 동    String upjong - 업종 | - AI 브로커(지능형 창업 후보지역 상권분석 어댑터)   - 해당 동에서 업종에 해당하는 상가 업소 목록을 가져온다 |

< 마이크로서비스 기반으로 샘플앱 빅데이터/AI서비스 브로커 Rest API Parameter>

 

### 샘플앱 빅데이터/AI 서비스 브로커 아키텍처 

   ![1558573328960](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/csbarch.png)

<마이크로서비스 샘플앱을 위한 빅데이터/AI 서비스 브로커 아키텍처>