# 마이크로서비스 스튜디오 활용 가이드

 

## 마이크로서비스 스튜디오 개요

개발지원 플랫폼에서는 마이크로서비스 아키텍처 기반 웹 개발을 지원하는 마이크로서비스 스튜디오를 제공한다. 마이크로서비스 스튜디오는 애플리케이션 개발부터 배포, 운영 단계까지 지원하는 마이크로서비스 개발 지원 도구이다. 일반적인 애플리케이션 개발은 하나의 애플리케이션으로 되어 있지만 마이크로서비스는 여러개의 애플리케이션을 구성하여 하나의 서비스 또는 여러 서비스를 지원하는 시스템을 구성할 수 있다. 

기존 모놀리식 애플리케이션에서는  단순한 수정사항이나 서비스 추가의 경우에도 전체를 빌드해야 하지만 마이크로서비스 애플리케이션은 아주 작은 단위의 여러 애플리케이션으로 구성되어 있어 해당되는 애플리케이션만 수정하고 빌드하고 배포한다. 이런 작업이 가능하려면 각각의 앱 간의 네트워크, 환경설정, 등록정보 등에 규칙성이 있어야 하고 개발자들도 정해진 규칙이 있으면 적용해야 한다.

클라우드 플랫폼(PaaS)상에서 마이크로서비스 아키텍처를 적용한 개발 및 운영은 일반적인 개발보다 훨씬 빠르고 고품질의 개발을 수행할 수 있다. 

마이크로서비스 스튜디오를 이용하면 다음과 같은 장점이 있다. ;

-  개발 환경 설정 시 클라우드 플랫폼 활용을 아주 짧은 시간에 설정이 가능
- 서비스 브로커를 이용한 DBMS, MESSAGE QUEUE 의 쉬운 사용
- 쉬운 마이크로서비스 애플리케이션 환경 구성
- 개발에만 집중
- PaaS 플랫폼과 완전한 통합 지원
- 클라우드 상에서 개발부터 운영까지 전 라이프사이클 관리



## 마이크로서비스 스튜디오 아키텍처 

마이크로서비스 스튜디오는 Spring Cloud와 Cloud Foundry를 적용하였고 사용자 편의성을 고려하여 비주얼 편집기 기능을 개발하였다. Spring Cloud는 마이크로서비스 아키텍처 개발을 지원하는 다양한 컴포넌트를 갖고 있으며 이 서비스들을 Cloud Foundry의 모듈 및 서비스로 연동되어 있다. 

마이크로서비스 스튜디오는 Cloud Foundry의 모듈 및 서비스와 맵핑을 위해 서비스 브로커 기술을 적용하였다. 마이크로서비스 스튜디오 아키텍처는 다음과 같다.

![](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/MSA_Architecture.png)

- 마이크로서비스 스튜디오는 가시화 도구(비주얼 편집기)를 이용하여 애플리케이션과 서비스의 관계를 구성할 수 있으며 Cloud Foundry에 푸시된 애플리케이션과 마켓에 등록된 서비스를 기본으로 사용할 수 있다. 
- 마이크로서비스 스튜디오는 마이크로서비스 구성 시 API Gateway Server, Registry Service, Config Service 가 앱으로 자동 생성하고 화면상에서는 Gateway만 노출된다.
- 마이크로서비스 구성 시 프론트엔드 앱과 백엔드 앱을 연결하려면 반드시 게이트웨이를 거쳐서 정의해야 한다. 



## 마이크로서비스 스튜디오 주요 기능

마이크로서비스 스튜디오의 기본 기능은 PaaS을 이용하여 배포된 애플리케이션과 PaaS에서 제공하는 서비스를 이용하여 마이크로서비스 아키텍처를 구성하는 기능이다. 마이크로서비스 아키텍처의 기본은 여러 개의 작은 단위의 애플리케이션을 연동하여 서비스 또는 제품을 구성하기 때문에 수많은 애플리케이션 간의 관계가 가시적으로 보여줘야 한다. 그리고, 이들 관계 설정으로 생성된 Registry 정보, Config 정보, API Gateway 정보를 바로 확인하고 수정할 수 있어야 한다. 

주요 기능은 다음과 같다. ;

- **비주얼 편집기능** : PaaS에 배포된 애플리케이션과 서비스를 이용한 드래그 앤 드롭 기능을 이용하여 마이크로서비스 아키텍처를 구성

- **시각화된 토폴로지 기능** : 마이크로서비스 아키텍처 구성이 완료되면 애플리케이션의 관계, 상태를 토폴로지 형태로 시각화하여 조회된다. 

- **장애 알림** : 애플리케이션의 서비스가 중지되었거나 어떤 장애로 인하여 정상적으로 동작하지 않는 경우 시각적인 효과(빨간색으로 표시됨)로 알려줌

- **REST API** : 마이크로서비스 아키텍처는 각각의 애플리케이션 간의 상호 인터페이스는 REST API를 통해 구현하고 API Mock Test 기능을 제공한다. 마이크로서비스 스튜디오는 swagger API Level 2 기준으로 정의되어 있다. 

- **API 관리** : 마이크로서비스 스튜디오에서 생성한 마이크로서비스에서 사용한 애플리케이션이 갖고 있는 API를 외부에 공개하기 위해 등록하는 기능과 등록된 API를 모니터링 기능을 통해 상태를 점검할 수 있다. 

- **API 공유** : 마이크로서비스 스튜디오에는 API 목록을 조회하는 기능을 제공하고 이 기능은 사용자가 자신이 만든 애플리케이션에 정의한 API를 외부에 공개할 수 있다. 마이크로서비스 생성 시 FRONTEND 앱에 포함된 URL을 통해 외부에 공개된다. 

- **Java 개발 가이드** : 마이크로서비스 스튜디오는 Java로 개발된 애플리케이션만 관리할 수 있고 마이크로서비스 아키텍처 기반 개발을 위한 가이드를 제공한다. Spring Cloud의 기본 기술을 적용하여 제공하고 있고 java 언어 기준의 필수 개발 가이드를 제공한다. **DOCS 메뉴 이용**

- **보안** : 백엔드 애플리케이션을 위한 Spring Security의 Basic Auth 적용. Config, Registry, Gateway Service 에도 Basic Auth 적용됨

- **PaaS-TA 기반** : PaaS-TA상에 배포된 애플리케이션의 환경 설정 값을 읽어서 마이크로서비스 스튜디오에서 사용하도록 설계되어 있어 개발 진행 과정에서 PaaS-TA를 이용하여 앱을 푸시하고 애플리케이션 수정 및 재배포와 같은 변경사항이 발생하면 반복적으로 PaaS-TA 를 이용한다. PaaS-TA의 기본 사용 방법을 알고 있어야 한다.  PaaS-TA 사용자 가이드를 참조한다.

  

### 문서 구성

- #### [1. 애플리케이션 개요](#애플리케이션-개요)

- #### [백엔드앱 개발](#백엔드앱-개발)

- #### [프론트엔드 앱 개발](#프론트엔드-앱-개발)

- #### [PaaS-TA에 앱 배포하기](#PaaS-TA에-앱-배포하기)

- #### [마이크로서비스 앱 구성](#마이크로서비스-앱-구성)

- #### [API 관리](#API-관리)

 

### 참고 문서

- 오픈데이터API 게이트웨이 시스템
- 빅데이터 및 AI기반 상권 분석 브로커
- 마이크로서비스 스튜디오



## 애플리케이션 개요

개발지원 플랫폼의 오픈데이터API 게이트웨이 포털과 마이크로서비스 스튜디오를 활용하는 방법에 대해 실제 개발된 애플리케이션을 이용하여 설명한다.  

소개하는 애플리케이션은 서울시 문화공간 정보를 검색하는 사이트로 서울시 열린데이터 광장에서 제공하는 서울시 문화공간 현황 API를 호출하여 다양한 유형의 문화공간 정보를 검색할 수 있는 사이트이다. 

서울시 문화공간에는 박물관, 공연장, 미술관과 같은 유형이 존재하고 무료로 이용할 수 있는 공간만 검색하거나 유료 공간도 검색할 수 있다. 

통합 검색 기능을 이용하면 단어만으로 지역, 문화공간 이름 및 주소(위치)도 확인할 수 있다.  문화공간 유형과 입장료의 무료/유료를 선택하여 상세 조건 검색 기능을 제공한다.

 *[애플리케이션 개발 프로젝트는 마이크로서비스 기반 개발을 위해 주요 기능을 분할하여 각각의 앱으로  개발을 수행한다.  여기에서는 프론트엔드앱과 백엔드앱 각각 1개씩 개별 개발하여 구축하는 순서로 설명한다.]*



샘플 애플리케이션에서 제공하는 주요 기능은 아래와 같다.

### 마이크로서비스 단위 분할하기

- **FRONTEND** : 문화공간 통합 검색, 상세 검색 결과를 조회할 수 있는 프론트 페이지 
- **문화공간정보조회** : 문화공간현황 API를 호출하여 데이터베이스에 업로드하고 데이터베이스 정보를 다양한 형태로 조회하여 결과를 얻을 수 있는 API를 정의하여 제공
- **위치정보** : 지도서비스를 이용하여 지도상에 내가 찾은 문화공간 위치 표시하기

위와 같이 개발 아이디어에는 여러 종류의 서비스를 제공하고자 하는 경우라도 짧은 시간에 많은 서비스를 제공하는 앱을 출시하는 것이 창업자에게는 어려움이 있기 때문에 마이크로서비스 기반 개발을 이용하여 우선 오픈할 서비스와 나중에 오픈할 서비스를 분류한다. 우선 개발이 가능한 서비스를 다시 마이크로서비스 단위로 분할하여 개발을 진행한다.



### 주요 사용 기술

공공데이터포털을 통해 제공하는 서울시 열린데이터광장의 서울시 문화공간 현황API를 이용하여 데이터를 수집하고 수집한 데이터는 데이터베이스에 업로드하여 등록한다.

\-       서울시 문화공간 현황 API

\-       MYSQL 서비스

\-       마이크로서비스 앱 분할 및 아키텍처 구성



### 개발지원 플랫폼 활용 마이크로서비스 앱 개발 프로세스

마이크로서비스 기반 개발을 위한 다양한 방법이 존재하지만 개발지원 플랫폼에서 제공하는 마이크로서비스를 활용하려면 적용 프로세스을 이해하고 적용되어야 한다.  

1. 마이크로서비스 단위로 앱 분할. 기본적인 마이크로서비스 단위 분할 패턴을 적용하여 분할한다. 본 튜토리얼의 연관 문서로 제공하는 '마이크로서비스 개요' 부분을 참조한다. [마이크로서비스 개요](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/microservice.md)]
2. 서비스 브로커 활용 개발인 경우 PaaS-TA 로그인 후 서비스 인스턴스를 생성한 후 서비스 인스턴스 접속정보를 확인한다. [[서비스 인스턴스 생성](#빅데이터-서비스-인스턴스-생성)]
3. 자체 IDE 활용하거나 eclipse 을 이용하는 경우 PaaS-TA에서 plugin을 제공하고 있으니 환경을 설정하여 준비한다. eclipse plugin 설치 방법은 PaaS-TA 3.5 가이드를 참조한다. [[Open PaaS 개발환경 사용가이드](https://guide.paas-ta.kr/guide-1.0-spaghetti/use-guide/open-paas)]
4. 코딩
   - 마이크로서비스 개발 가이드(Microservice Studio 페이지의 DocS 메뉴 참조)를 참조하여 필수 체크 항목 및  추가되는 내용을 적용한다. 만약 가이드를 따르지 않으면 마이크로서비스 앱 간의 연동된 부분(API 등)의 정보를 정확하게 가져오지 못한다. 
   - 마이크로서비스 앱 간의 API 연동이 필수이므로 각 각 앱에 적용할 API를 위한 필수 체크 항목을 반드시 적용한다.
5. PaaS-TA에 개발된 앱을 마이크로서비스 단위별로 각각 PUSH한다.  PUSH 과정에서 msa 환경변수를 정의하거나 PUSH완료 후에도 환경변수 변경은 가능하다. 앱 PUSH 방법은 아래 세가지를 제공한다.
   1. PaaS-TA 포털을 통한 앱 PUSH
   2. CF CLI을 통한 앱 PUSH --> 재배포 시에는 반드시 CF CLI을 이용해야 한다.
   3. eclipse Plugin을 통한 eclipse에서 Open PaaS 서버를 연동한 push --> 재배포 가능
6. 환경변수 msa = yes 를 추가한다. (PUSH  진행 중 또는 PUSH 후)
7. 마이크로서비스 스튜디오 페이지 접속 --> PaaS-TA 로그인 계정과 동일
8. 마이크로서비스 스튜디오를 통해 마이크로서비스를 추가한다. 
9. PaaS-TA에 PUSH된 앱 목록과 PaaS-TA에 등록된 서비스를 활용하여 마이크로서비스를 구성한다.
10. API 공개는 선택적 기능으로 개발이 완료된 마이크로서비스를 다른 사용자에게 공개하고자 하는 경우에 사용한다.[마이크로서비스 사용자 가이드](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/microserviceuser.md]

### 마이크로서비스 기반 개발

마이크로서비스 기반으로 개발을 위해 제공하는 서비스를 비지니스 영역, 데이터베이스 종속성 등을 고려하여 분할한다. 여기에서는 향후 확장할 서비스를 포함하여 총 3개의 앱으로 분할하여 개발한다고 간주한다.

사용자 UI제공을 위한 프론트앤드 앱과 창업지역 찾기 정보를 제공하는 백엔드 앱을 우선 개발영역으로 본다.

![](https://github.com/startupcloudplatform/Sample-App-Tutorial/tree/master/images/apigateway.png)



## 백엔드앱 개발

 

### 오픈데이터API 게이트웨이 시스템



#### 오픈데이터 API 게이트웨이 포털 사용 방법 

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

3)     오픈데이터 API 검색(서울시 문화공간 현황)

​       ![1558572796563](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/searchseoulspace.png)                  

\-       1. 오픈데이터 검색 창

\-       2. 오픈데이터 검색 결과



4)     서울시 문화공간 현황 API 상세 정보

​     ![1558572943817](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/seoulspacedetail.png)     

\-       1. 서울시 문화공간 현황 조회 API 상세 정보

\-       2. 즐겨찾기 추가, 데이터 신청, 취소



5)      예제 코드 조회

​      ![1558573046560](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/readcode.png)                                      



\-       1. 사용자 인증키

\-       2. 사용자 오픈 API

\-       3. 서울시 문화공간 예제 코드



### 서울시 문화공간 API 호출 방법

1)     서울시 문화공간 현황 조회 코드 입력 화면

​     ![1558573133977](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/storecode.png)                                                         

\-       1. 예제로 제공된 코드를 개발자가 필요한 부분에 입력 및 파싱한 화면

 

2)     API 실행 결과 화면

![1558573244893](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/runapi.png)

   \-       1. 개발자가 입력 및 파싱 수행 한 결과 화면

 

### 서울시 문화공간 현황 API 상세 

#### API 목록

| **URL**                                   | **파라미터**                                          | **설명**                                  |
| :---------------------------------------- | ----------------------------------------------------- | ----------------------------------------- |
| /api/search/all                           |                                                       | 문화공간전체 조회                         |
| /api/search/all/count                     |                                                       | 문화공간 전체 개수                        |
| /api/search/list?query                    | 검색어 query                                          | 키워드 조회                               |
| /api/search/name/list?query=              | 문화공간명 query                                      | 문화공간명칭 조회                         |
| /api/search/type/list?query=              | 장르분류명 query                                      | 시설분류(장르)조회                        |
| /api/search/address/list?query=           | 주소 query                                            | 주소로 문화공간조회                       |
| /api/search/fee/list?query=               | 입장요금 query                                        | 요금일치정보 조회                         |
| /api/search/condition?type=&fee=&address= | 장르분류코드 code<br />입장요금 fee<br />주소 address | 장르분류, 입장요금, 주소 조건을 통한 조회 |
| /api/search/group/type                    |                                                       | 시설분류 그룹조회                         |
| /api/search/group/fee                     |                                                       | 입장요금 그룹조회                         |
| /api/facilities/list                      |                                                       | 시설분류 목록                             |
| /api/facilities/update                    |                                                       | 데이터 업데이트                           |
| /api/facilities/delete                    |                                                       | 데이터 삭제                               |
| /api/facilities/delete/{code}             | 코드값 code                                           | 시설분류코드 삭제                         |

< Rest API Parameter>

 

## 프론트엔드 앱 개발

본 튜토리얼은 eclipse 4.10.0을 기준으로 작성되었으며 PaaS-TA 에서도 WEB IDE를 제공하고 있으며 활용이 가능하다. 다른 익숙한 IDE를 활용해도 무방하다.



### 개발 환경 요구사항

| 요구사항     | 버전  |
| ------------ | ----- |
| AngularJS    |       |
| Java         | 1.8   |
| Spring Boot  | 1.5.9 |
| Spring Cloud | 1.6.1 |
| swagger API  | 2.0.0 |

- ###### Open API 게이트웨이 시스템

​       서울시 문화공간 현황( http://203.245.1.104:3000/ )

- ###### Open PaaS 

​      PaaS-TA 3.1, 3.5(Penne)

​       https://guide.paas-ta.kr/guide-3.5-penne

 

### eclipse IDE 환경 구성

여기에서는 eclipse 4.10 버전을 이용하여 프로젝트 생성하는 방법을 설명한다. Eclipse에서 Maven project를 생성하고 JAVA 1.8을 적용한다.  

eclipse IDE에서 프로젝트를 직접 생성하려면 Project Explorer에서 마우스 우클릭 후 New > Project.. 을 선택한다. Maven Project을 선택하면 기본 Maven 환경이 구성된다. (사전에 Maven 설치가 완료되어 있어야 한다.)

Maven Project 생성 시 

- GroupId : com.example.sample 로 등록한다.
- ArtifactId : frontend
- Package : com.example.sample 로 등록한다. 



### Java 필수 항목 코딩

마이크로서비스 앱 개발은 여러 개의 앱을 구성하여 구동하는 방식으로 개발 환경 설정 시 여러 필수 체크 부분이 존재한다. 특히, JAVA Spring cloud 기반 코딩을 위한 dependency를 정의한다. 기본으로 pom.xml 파일이 생성되었을 것이다. 이 파일을 오픈하고 아래 내용을 붙여넣기 한다.

##### pom.xml 파일 수정

초기 환경 구축 시 pom.xml에 마이크로서비스 앱 개발을 위한 <parent></parent>와 <properties></properties> 를 아래의 내용을 복사하여 pom.xml에 붙여넣기 한다.  JAVA: 1.8이상, Spring Boot: 1.5.13, Spring Cloud: Edgware.RELEASE 는 필수 체크 항목이다. 

```
   <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.9.RELEASE</version>
        <relativePath/> <!-- lookup parent from repository -->
   </parent>
   
   <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <java.version>1.8</java.version>
        <spring-cloud.version>Edgware.RELEASE</spring-cloud.version>
   </properties>
```



java spring cloud 기반 코딩을 위한 필수 dependency 정의를 위해 아래 내용을 복사하여 pom.xml에 붙여넣기 한다. 

```
<dependencies>
  <!-- required start -->
  <dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-config</artifactId>
  </dependency>
  <dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-eureka</artifactId>
  </dependency>
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
  </dependency>
  <dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-hystrix</artifactId>
  </dependency>
  <dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger2</artifactId>
    <version>2.3.1</version>
  </dependency>
  <dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
  </dependency>
  <dependency>
    <groupId>io.pivotal.spring.cloud</groupId>
    <artifactId>spring-cloud-services-cloudfoundry-connector</artifactId>
    <version>1.6.1.RELEASE</version>
  </dependency>
  <dependency>
    <groupId>io.pivotal.spring.cloud</groupId>
    <artifactId>spring-cloud-services-spring-connector</artifactId>
    <version>1.6.1.RELEASE</version>
  </dependency>  
  <!-- required end -->
</dependencies>
```



#####  annotation 정의를 위한 Java 클래스 생성

java 프로젝트 생성 후 디폴트로 생성된 App.java 파일에 annotation을 정의한다. annotation은 java spring cloud 의 eureka 기능 사용과 rest api 명세를 위한 swagger 필수 annotation 이다. App.java의 기존 내용을 모두 삭제하고 아래 내용을 복사하여 붙여넣기 한다. (소스코드로 배포한 파일에는 클래스이름이 SampleApplication.java로 되어 있음.)

@EnableDiscoveryClient, @EnableCircuitBreaker, @EnableSwagger2

```
package com.example.sample.front;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.cloud.client.circuitbreaker.EnableCircuitBreaker;
import org.springframework.cloud.client.discovery.EnableDiscoveryClient;
import org.springframework.cloud.client.loadbalancer.LoadBalanced;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.client.RestTemplate;
import springfox.documentation.builders.PathSelectors;
import springfox.documentation.builders.RequestHandlerSelectors;
import springfox.documentation.spi.DocumentationType;
import springfox.documentation.spring.web.plugins.Docket;
import springfox.documentation.swagger2.annotations.EnableSwagger2;

@EnableDiscoveryClient
@EnableCircuitBreaker
@SpringBootApplication
public class App {

    @LoadBalanced
    @Bean
    RestTemplate restTemplate() {
        return new RestTemplate();
    }

    public static void main(String[] args) {
        SpringApplication.run(App.class, args);
    }
}

@Configuration
@EnableSwagger2
class SwaggerConfig {
    @Bean
    public Docket api() {
        return new Docket(DocumentationType.SWAGGER_2)
                .select().apis(RequestHandlerSelectors.any())
                .paths(PathSelectors.ant("/api/**"))
                .build();
    }
}
```

**@EnableDiscoveryClient**    // Service Discovery 정의   

Eureka 서버가 서비스를 탐색할 때 사용한다. 서비스 검색(Service Discovery)은 마이크로서비스 기반 아키텍처의 핵심 기술요소로  각 클라이언트 또는 일부 형식을 수동으로 구성하는 것은 매우 어려울 수 있다. Eureka는 Netflix 서비스 검색 서버 및 클라이언트로 서버는 등록된 서비스에 대한 상태를 다른 서버로 복제하여 각 서버가 HA(고가용성) 구성 및 배치를 할 수 있다
Eureka client설정: Eureka Server가 작동하고 있는 상태에서 Eureka client를 시작하면 Eureka Server의 Registry에 등록된다.  @EnableDiscoveryClient을 활성화시킨 상태에서서 RestTemplate Bean 에 @LoadBalanced만 달아주면 모든 설정을 Spring Boot에서  자동으로 해준다.

**@EnableCircuitBreaker**   // 서비스 부하 차단기 정의    

Netflix는 Circuit Breaker 패턴을 구현을 위한 Hystrix라는 라이브러리를 만들 수 있다. 마이크로서비스 아키텍처에서는 다음 예제와 같이 여러 개의 서비스 호출 계층을 갖는 것이 일반적이다. 

ex) Hystrix Stream 샘플 예제

![Hystrix](https://raw.githubusercontent.com/spring-cloud/spring-cloud-netflix/master/docs/src/main/asciidoc/images/Hystrix.png)

[출처:<https://cloud.spring.io/spring-cloud-netflix/multi/multi__circuit_breaker_hystrix_clients.html>]



**@LoadBalanced**       // Netflix Ribbon을 자동 적용, 

Service Discovery을 IP대신 찾아서 서비스이름으로 사용할 수 있다.  마이크로서비스 환경에서 효과적으로 사용하기 위해서는, @LoadBalanced 어노테이션을 사용해야 한다. 이 annotation으로 인하여, Netflix Ribbon을 자동적으로 사용할 수 있게 되고, 서비스 발견을 IP대신 서비스 이름으로 할 수 있게 된다.

**@EnableSwagger2**    // swagger API 정의

Swagger2는 RESTful 웹 서비스 용 REST API 문서를 생성하기 위해 사용되는 오픈 소스 프로젝트이다. 웹 브라우저를 통해 RESTful 웹 서비스에 액세스 할 수 있는 사용자 인터페이스를 제공한다. Spring Boot 애플리케이션에서 Swagger2를 사용하려면 dependency을 추가해야 한다. 앞에서 설명한 pom.xml 에 추가한다. 

```
 <dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger2</artifactId>
    <version>2.3.1</version>
 </dependency>
```



##### manifest.yml 생성하기

PaaS-TA에 앱을 푸시할때 사용하는 환경설정 파일이며 manifest.yml 이름으로 생성한 후 아래 내용을 복사한 후 붙여넣기 한다.

**필수 환경설정변수 : msa**

```
---
applications:
  - name: front
    memory: 1G
    path: target/front-0.0.1-SNAPSHOT.jar
    env:
      msa: true
```



##### application.properties 생성하기

마이크로서비스 앱 이름 정의하는 파일로 application.properties 이름으로 생성한다. 

소스코드 경로 : src/main/resources/application.properties

```
spring.application.name=front
```



#### RestController 정의

마이크로서비스는 여러 앱을 API로 연동되어 있기 때문에 controller를 정의해야 한다. 

```
package com.example.sample;

import org.json.simple.parser.ParseException;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.cloud.context.config.annotation.RefreshScope;
import org.springframework.http.*;
import org.springframework.util.Base64Utils;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.ResponseBody;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.client.RestTemplate;
import org.springframework.web.util.UriComponents;
import org.springframework.web.util.UriComponentsBuilder;
```

**@RestController**

REST API는 외부에서 정해진 호출 방식으로 특정 URI를 통해서 사용자가 원하는 정보를 제공하는 방식이다.  REST 방식의 서비스 제공이 가능한 것을 Restful이라고 한다. 

```
@RestController
@RefreshScope
public class TestCntroller {
	
	@Autowired
    private RestTemplate searchClient;
	//마이크로서비스 config쪽에서 basic auth정보 가져오는 부분
    //spring apllication property 문법 참조
    @Value("${gateway.basic.user: }")
    String user;

    @Value("${gateway.basic.password:}")
    String password;

    Object responseReturn = null;
    //HttpHeader를 BasicAuth추가하는 함수
    private HttpHeaders getHeaders(){
        String basicAuth = String.format("%s:%s", user, password);
        String base64Auth = Base64Utils.encodeToString(basicAuth.getBytes());

        HttpHeaders headers = new HttpHeaders();
        headers.setContentType(MediaType.APPLICATION_JSON);
        headers.add("Authorization", String.format("Basic %s", base64Auth));
        postConstruct();
        return headers;
    }
 }
```



마이크로서비스 기반 개발을 위한 해당되는 클래스, pom.xml, application.properties 등의 기본적인 정의가 완료되었다면 나머지 코딩은 개발자가 원하는 내용에 따라 달라질 수 있어 본 문서에서는 샘플앱에 포함된 다른 클래스에 대한 설명은 생략한다. 

필수 정의항목과 나머지 코딩이 완료되면 PaaS-TA 서버와 연동하여 앱을 배포하거나 개별로 빌드를 수행한 후 빌드된 파일을 이용하여 PaaS-TA 에 배포해도 된다. 



## PaaS-TA에 앱 배포하기

코딩이 완료된 소스를 Maven Build를 이용하여 *.jar를 생성한다. 생성된 *.jar 파일을 PaaS-TA에 push한다. PaaS-TA를 이용할 수 있는 환경에서는 포털사이트를 통해서도 앱 push가 가능하다. 여기에서는 Cloud Foundry Cli를 통해서 Push 하는 방법을 설명한다.

 *[PaaS-TA 사용자가이드 참조](https://guide.paas-ta.kr/guide-3.5-penne)*

#### PaaS-TA 포털 로그인

접속 가능한 PaaS-TA 사용자 포털을 이용하여 앱을 푸시할 수 있다. 계정을 갖고 있다면 포털 로그인이 가능하다. 



#### CF Login

PaaS-TA 계정을 갖고 있다면 Cloud-Foundry 접속 경로를 통해서 로그인한다. 

```
$ cf login -a 접속URI --skip-ssl-validation
API endpoint: 접속URI
Email>계정
Password>비밀번호
Authenticating...
OK

Targeted org system
Targeted space paas-ta

API endpoint:   https://api.k-cloud.org(API version: 2.116.0)
User:           admin
Org:            system
Space:          paas-ta
```



#### 앱 Push

소스코드 경로로 이동하고 앱 push 명령어를 입력하여 앱을 push한다. 이때, manifest.yml이 정의되어 있는지 확인한다. PaaS-TA 앱 push를 위해서는 이 파일이 필수이다.

```
$ cf push startup
```

buildpack호출 과정과 Configuration 설정과정을 거쳐 앱이 컨테이너에 push된다. 앱이 정상적으로 push되었는지 확인한다. 

```
$ cf app startup
Showing health and status for app startup in org Org1 / space DEV as admin...

name:              startup
requested state:   started
routes:            uvaj4b89pd.k-cloud.org
last uploaded:     Fri 26 Apr 16:36:37 KST 2019
stack:             cflinuxfs2
buildpacks:        java_buildpack-v4-15

type:           web
instances:      1/1
memory usage:   1024M
     state     since                  cpu    memory       disk           details
#0   running   2019-04-26T07:37:07Z   0.2%   217M of 1G   183M of 512M
```



#### 환경변수 정의

manifest.yml 파일에 정의된 사용자정의 환경변수가 정의되어 있는지 확인한다.

```
$ cf env startup
```

결과 예시

```
{
 "VCAP_APPLICATION": {
  "application_id": "13e72952-9128-4406-b5a1-a0927952512a",
  "application_name": "startup",
  "application_uris": [
   "uvaj4b89pd.msxpert.co.kr"
  ],
  "application_version": "e1b5522f-23df-48c0-8003-8e67867c31d7",
  "cf_api": "https://api.k-cloud.org",
  "limits": {
   "disk": 512,
   "fds": 16384,
   "mem": 1024
  },
  "name": "startup",
  "space_id": "46ad022f-bf06-43c9-b2f8-1d4809c96daf",
  "space_name": "DEV",
  "uris": [
   "uvaj4b89pd.k-cloud.org"
  ],
  "users": null,
  "version": "e1b5522f-23df-48c0-8003-8e67867c31d7"
 }
}

User-Provided:
msa: true
```



## 마이크로서비스 앱 구성

PaaS-TA에 push된 앱은 마이크로서비스 스튜디오를 이용하여 마이크로서비스를 구성한다. 마이크로서비스 구성을 위해 개발된 프론트앤드 앱, 백엔드 앱 모두 PaaS-TA에 push되어 있어야 한다. 

마이크로서비스 스튜디오 사용 방법은 [사용자 가이드]()를 참조한다.

#### [마이크로서비스 접속하기]() 



### 마이크로서비스 구성 하기

1. 마이크로서비스 스튜디오를 접속하면 초기 화면은 CATALOG 목록이 기본 페이지이다. 

2. 추가 버튼을 이용하여 마이크로서비스를 생성하여 구성한다.

   ![1557810254136](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/msamain_new.png)

3. 생성 화면에서 필수 입력값을 채워서 생성한다. 이때 PaaS-TA에 자신이 권한을 갖고 있는 조직과 영역을 지정해야 한다. 

![1557810443245](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/msaadd.png)

1. 초기 화면에는 Gateway 아이콘만 화면에 보일 것이다.

#### 드래그 앤 드롭 기능 사용하기(앱 배치)

1. 등록된 앱목록에서 앱을 디자인 영역으로 드래그 앤 드롭 기능을 이용하여 배치한다.
2. App List을 클릭하면 PaaS-TA를 이용하여 푸시한 앱 목록이 보일 것이다. 프론트엔드 앱과 백엔드 앱이 보일 것이다.

![1557810643268](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/msaapplist_new.png)

1. 둘 다 화면에 배치한 후 앱 간의 네트워크 정보는 선으로 연결한다. 선을 연결할 때는 시작하는 앱을 **Shift키**를 누른 상태로 다른 앱으로 마우스를 이동한다.
2. 네트워크 연결 시에는 반드시 순서를 지켜야 하는데 Gateway를 통해 Registry에 등록되기 때문에 프론트앤드 앱과 Gateway를 연결해야 하고 Gateway와 백엔드 앱을 연결해야 한다. 

#### 서비스 구성하기

PaaS-TA에 배포된 서비스 브로커는 모두 사용할 수 있다. 창업 플랫폼으로 새로 추가된 빅데이터 서비스 브로커와 AI기반 상권 분석 브로커 등을 이용할 수 있다. 본 샘플 앱에서는 빅데이터 및 AI서비스 브로커를 이용하여 관련된 서비스를 같이 구성해야 한다.

1. 마이크로서비스 구성 화면의 오른쪽 메뉴에서 Service 를 선택한다.

2. 서비스 목록이 조회된다. 앱 구성과 마찬가지로 드로잉 영역으로 해당 되는 서비스를 드래그앤 드롭하여 배치한다.

3. 서비스를 연결하는 경우 백엔드 앱을 통해 서비스를 연결해야 한다. 

4. 위의 과정을 통하면 마이크로서비스 구성이 완료된다.

   ![](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/msa_design.png)



### 마이크로서비스 조회 및 수정

생성과정을 통해 마이크로서비스 구성이 완료되었다면 Deploying 까지 완료된 상태이다. 외부에 오픈 가능한 도메인을 사용했다면 웹사이트 URL를 통해 어디에서든지 접속이 가능하다.

마이크로서비스 상세 조회화면에는 아래와 같은 정보를 확인할 수 있다.

- App

  App 목록을 통해 접근 가능한 URL을 확인할 수 있다. 

  ![](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/appdesc.png)

- Service 

​       마이크로서비스에 포함된 모든 서비스 목록을 제공한다.

- App & Service

- Network

- App Rest API

  API 호출 테스트를 실행할 수 있다. 

  ![apitest](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/apitest_new.png)

- Gateway

- Registry

- Configuration

- App Logging

​      마이크로서비스로 구성된 앱의 로그 정보를 뷰어롤 통해 제공한다. 동시에 여러개의 앱의 로그를 볼 수도 있다.

![](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/applog.png)



#### 마이크로서비스 수정하기

이미 구성을 완료한 경우 수정 화면을 통해서 기존 마이크로서비스 구성 상태를 변경할 수 있다. 상단 메뉴바에서 CATALOG를 선택하고 해당되는 마이크로서비스 목록의 이름을 클릭한다. 

조회화면에서 연필모양 아이콘을 클릭하면 수정화면으로 변경된다.

![1557811325022](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/msaupdate_new.png)

수정화면에서 앱을 시작, 종료 상태를 변경할 수 있고 현재 페이지의 결과를 완전히 삭제할 수도 있다. 드로잉 영역의 이미지를 확대하거 축소하는 경우(+,-) 아이콘을 이용한다. 



### REST API 테스트 기능 활용 하기

튜토리얼에서 소개하는 샘플앱은 프론트엔드 앱과 백엔드 앱 두개로 구성되어 있다. 백엔드 앱에는사용한 빅데이터 서비스 브로커를 이용하여 창업지역API 를 호출할 수 있게 개발되었고 프론트엔드 앱에서는 오픈된 API를 호출하여 프론트 영역에 사용자가 원하는 정보를 호출하도록 개발되었다. 개발하면서 정의한 API 목록을 swagger API로 조회하고 테스트해볼 수 있는 기능을 제공한다. 



### 외부 API 활용

마이크로서비스 추가화면에서 외부 api 추가하는 기능을 사용할 수 있다. 이 샘플앱에서는 외부 API를 활용하지 않았지만 개발 범위 내에 외부 API를 활용할 필요가 있다면 아래와 같은 절차를 이용하면 외부 API를 활용할 수 있다. 

1. 마이크로서비스 추가 화면 또는 수정화면을 이용한다.
2. 오른쪽 메뉴에서 API 메뉴을 선택한다. 
3. 사용 가능한 API 목록이 조회된다. 
4. 사용할 API 오른쪽 옆에 + 버튼을 누르면 API를 사용할 수 있는데 접속할 계정을 등록해야 한다. 
5. 여기에서의 계정은 사용자가 추가한 API를 접속할 때 이용하는 계정 정보이다. 유출되지 않도록 해야 하고 잊어버리지 않도록 주의하자.

![1557812323113](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/bauth.png)

6. 아이콘을 누르면 API 목록과 상세 정보를 조회할 수 있다.

   

## API 관리 

마이크로서비스 기반으로 개발된 앱을 다른 사용자에게 공유를 위해 공개 설정을 할 수 있다. 공개 설정은 프론트엔드 앱에 정의한 API 설정 정보 기반으로 공개된다. 프론트엔드 앱에 백엔드 앱 호출 API를 정의해야 한다. 

프론트엔드 앱 개발 시 Controller에 정의한 @GetMapping 정보가 공개된다. 

API 공개 구조는 다음과 같다. 

![](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/apisystem.png)

### 다른 앱에 정의된 API 호출

다른 앱에서 정의한 API를 활용하여 개발 시 포함할 때는 API경로에 유의해야 한다. 본 튜토리얼에서 소개하고 있는 샘플 앱의 경우 주요 기능을 수행하는 API는 백엔드 앱에 정의되어 있다. 프론트엔드 앱에서 백엔드 앱의 API를 호출은 게이트웨이를 통해서 호출이 가능하기 때문에 게이트웨이 경로를 알고 있어야 한다. 

#### 게이트웨이 경로

게이트웨이 경로는 호출하고자 하는 앱이 마이크로서비스 스튜디오에 이미 구성되어 있어야 한다. 앱배포와 구성을 진행하면 자동으로 게이트웨이가 생성될 것이다. 마이크로서비스 스튜디오에서 마이크로서비스 상세 페이지의 오른쪽 메뉴에서 Registry 메뉴를 선택한다. 등록된 게이트웨이를 확인할 수 있다. 

프론트엔드 앱에 @GetMapping("api/sido")를 통해 백엔드 앱으로 부터 데이터를 받아온다.

```
@GetMapping("/api/sido")
public @ResponseBody
.....
```

```
@GetMapping("/api/sangho")
public @ResponseBody
.....
```

위와 같이 개발 소스코드를 정의하게 되면 API 등록 시 위의 정보를 호출하게 된다. 



#### API 등록--관리자 메뉴

자신이 등록한 마이크로서비스에 위에서 설명한 API 공개를 위한 조건에 부합이 된다면 API 등록을 통해 다른 사용자에게도 API를 공개할 수 있다. 아래 과정을 통해 API를 등록하면 다른 사용자에게 API목록이 조회된다. 

1. 마이크로서비스 상단 메뉴의 오른쪽에 환경설정 아이콘을 클릭하면 마이크로서비스 API관리 메뉴가 있다. 
2. 이 메뉴을 선택하면 등록된 API 목록 화면이 나오고 등록버튼을 볼 수 있다. 
3. 등록 버튼을 눌러서 등록할 API가 있는 앱이 배포된 조직을 선택한다. 
4. 다음 버튼을 누르면 공개할 API의 세부 정보를 등록할 수 있다. 
   ![1557813404373](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/addapi.png)
5. 필수입력값을 잘 확인하여 값을 입력한다. 
6. 마이크로서비스 Frontend 부분에서 URL 부분의 리스트를 선택한다. 이 리스트에 나오는 값은 마이크로서비스 구성 시 Frontend App 의 URL을 자동으로 가져온다. 
   ![1557813500584](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/fronturl.png)
7. 해당 URL을 선택한다.
8. 등록 버튼이 활성화되면 클릭한다.
9. 등록된 결과는 상단 메뉴의 API을 통해 확인할 수 있다.



## 마이크로서비스 운영

샘플앱을 기준으로는 프론트엔드 앱과 백엔드 앱 두개의 앱을 실제 배포된 서비스의 운영은 PaaS-TA 상에서 가능하다. PaaS-TA에서 제공하는 운영 서버의 앱 상태를 관리하는 것이다. 마이크로서비스 스튜디오에서는 운영서버에 배포된 각각의 앱과 앱 간의 관계를 정의한 게이트웨이, 서비스 디스커버리를 위한 레지스트리 등의 정보에 장애가 발생하면 앱 상태를 정상과 다른 색상의 앱으로 표시된다. 

앱 상태에 따라 서비스를 재시작하거나 중지는 마이크로서비스에서 운영이 가능하다. 앱이 변경되어 재배포를 실행하려면 PaaS-TA에서 제공하는 기존 앱의 재배포 기능을 사용하거나 CF CLI을 이용하여 앱을 변경된 파일을 재배포할 수 있다. 마찬가지로, eclipse를 이용하는 경우에도 변경된 소스 기반으로 Open PaaS 서버에 재배포를 실행한다. 

### 앱 재배포

- #### eclipse 에서 재배포

  eclipse 를 이용하여 기존 앱을 재배포하려면 Open PaaS 서버에 이미 등록되어 있는 앱을 삭제하지 말고 실행해야 한다. Open PaaS 서버를 eclipse와 연동하게 되면 서버의 앱과 실행하는 단계에서 현재상태와 동기화되기 때문에 기존에 배포된 앱을 실제 삭제하는 경우를 제외하고는 Remove.. 하지 않도록 주의한다.

- #### 재배포 방법

  eclipse의 Servers탭을 선택하고 Open PaaS라고 되어 있는 서버를 선택한다. Open PaaS 서버에서 실행되는 앱 목록을 확인할 수 있다. 소스코드 변경이 완료되었다면 해당 앱을 선택하고 마우스 우클릭하면 배포라는 메뉴가 보일 것이다. 이 메뉴를 실행한다. 

  ![1557896286937](https://github.com/startupcloudplatform/Sample-App-Tutorial/blob/master/images/eclipse_deploy.png)



### PaaS-TA 포털을 이용한 운영

PaaS-TA 사용자 포털을 이용하면 자신이 PaaS-TA에 배포한 앱과 마이크로서비스로 구성하면서 생성된 앱을 모두 조회할 수 있다. PaaS-TA 기반의 마이크로서비스 구성 시 필수로 생성된 Registry, Gateway, Gateway 앱 현황을 확인할 수 있다. 자신이 배포한 앱과 마이크로서비스에서 자동으로 생성된 앱 구분은 앱 이름으로 구분된다. 

#### 마이크로서비스에서 자동으로 생성된 앱

- Registry : registryapp + 'guid' 
- Config : configapp + 'guid'
- Gateway : gatewayapp + 'guid'

사용자가 생성한 앱과 같이 운영 관리 대상이 되므로 임의로 삭제하거나 이름을 변경하는 경우 마이크로서비스 앱이 정상적으로 동작하지 않을 수 있다. 

#### 마이크로서비스에서 자동으로 생성된 서비스 

- Registry Server : registry-server로 명명되어 있고 registry 관리하는 서비스 
- Config Server : config-server로 명명되어 있고 configuration을 관리하는 서비스

포털 화면의 대시보드 페이지에서 서비스 탭을 눌러서 확인할 수 있다. 

