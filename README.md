# 이 프로젝트는

> 개인 개발용 Demo 프로젝트 입니다.

## 기술 사양

### 개발 환경

1. 개발 언어는 **자바** 이며, JDK 버젼은 **_8_** 입니다.
2. 개발 IDE
   * IntelliJ 를 기본으로 합니다.
   * [Visual Stuido Code](https://code.visualstudio.com/) (이하 VSC) 는 IntelliJ 의 대안으로 사용 가능하며, 추가 플러그인 설치로 코드 및 프로젝 문서 작성에 사용 가능합니다.
3. 코드 형상 관리
   * 코드 형상관리는 [Git](https://git-scm.com/) 을 이용합니다.
   * 원격 저장소는 [Github](https://about.github.com/) 으로 관리됩니다.
4. 코드 빌드
   * 코드 빌드 및 라이브러리 의존성 관리를 위해 [Maven](http://maven.apache.org/) 을 사용합니다.
   * 지속적인 통합 빌드는 [Jenkins](https://jenkins.io/) 로 구축된 빌드 시스템에서 처리할 예정입니다.
5. 코드 품질 관리
   * 코드 통합 빌드시 [SonarQube](https://www.sonarqube.org/) 를 이용하여 지속적으로 코드 품질에 대한 정적 분석을 수행하여 코드 품질을 관리합니다.
6. Database
   * 개인 개발환경에서의 Database 는 MySQL 를 아래 명령어와 같이 Docker 로 구동하여 사용합니다.

    ```bash
    docker run -d \ # Daemon 모드로 MySQL Docker Container 실행
        -p 3306:3306 \ # 3306 포트 연결
        -e "MYSQL_ROOT_PASSWORD=xxxxxxx" \ # Database ROOT 비밀번호 설정
        --name demo mysql\ # Docker Container 이름 설정
        --character-set-server=utf8mb4 \ # Database 기본 CharacterSet 을 UTF8 로 설정
        --collation-server=utf8mb4_unicode_ci # Database 기본 Collation 을 UTF8 로 설정
    ```
7. RESTful 도구
   * API 구현 및 테스트를 위해 [POSTMAN](https://www.getpostman.com/apps) 을 이용합니다.
8. Cache
   * 개인 개발환경에서의 Cache 는 Redis 를 아래 명령어와 같이 Docker 로 구동하여 사용합니다.

   ```bash
   docker run -d \ # Daemon 모드로 Redis Docker Container 실행
       --name mohaji-redis \ # Docker Container 이름 설정
       -p 26379:6379 \ # 포트 충돌을 방지하기 위해 Docker Container 6379 포트를 Docker Host 의 26379 로 연결
       redis:3 # Redis Docker Container Image 중 "3" 으로 tag 가 지정된 버젼 사용
   ```
9. 레이아웃 템플릿
  * `Sitemesh`를 이용한 Layout Template를 사용합니다.

  ```bash
   # sitemesh.xml 설정
   
   # decorator.xml 설정
  ```

### 주요 Framework

* [IntelliJ](https://www.jetbrains.com/ko-kr/idea/download/#section=windows)
  * Spring 을 이용한 프로젝트 구성의 기본이 프레임워크입니다.
* [MyBatis](http://www.mybatis.org/mybatis-3/)
  * Persistence Layer 를 담당하는 라이브러리로 Database 처리에 사용합니다.
* [Jackson](https://github.com/FasterXML/jackson)
  * JSON, CSV, XML 등의 serialization / deserialization 처리에 사용합니다.
* [POI](https://poi.apache.org/)
  * Excel 파일 입 / 출력에 사용합니다.
* [iText](https://itextpdf.com/)
  * PDF 파일 생성에 사용합니다.

### 주요 기술

* [Docker](https://www.docker.com/)
  * 즉시 배포 가능한 격리된 환경의 경량화된 가상화 기술로 본 프로젝트에서는 서비스 이미지 생성 및 개발환경 인프라 구성에 사용합니다.

## 개발 주요 인프라

> 개발에 사용되는 인프라는 아래와 같으며 _**코드 형상관리 시스템에서 계정을 할당받아 SSO 로 로그인 처리**_ 한다.

1. 코드 형상 관리 (GitLab): <https://git.mohaji.kr/>
