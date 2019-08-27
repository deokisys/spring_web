# spring_web

---

- 목차
  - 설정
    - jdk설치
    - tomcat8설치
    - sts3설치
    - db설치
  - 시작
  - 출처

---

- 설정

1. JDK설치

   1. https://www.oracle.com/technetwork/java/javase/downloads/index.html
   2. 8버전으로 os에 맞게 설치

2. Tomcat8 설치

   1. http://tomcat.apache.org/

   2. 8버전 설치 

      1.  core - tar.gz파일 압축 해제
      2. 설치 순서

      | 1    | sudo mkdir -p usr/local                                      | Tomcat을 설치할 폴더를 생성함 (Password는 맥북에 설정된 암호를 입력하면 됩니다.) |
      | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
      | 2    | sudo mv ~/Desktop/apache-tomcat-8.5.39 /usr/local            | 바탕화면으로 옮겨놨던 tomcat폴더를 윗줄에서 생성한 폴더로 이동함 |
      | 3    | sudo rm -f ~Library/Tomcat                                   | Library안에 Tomcat이 혹시라도 있을 경우를 대비해 삭제함      |
      | 4    | sudo ln -s /usr/local/apache-tomcat-8.5.39 /Library/Tomcat   | local에 옮겨놨던  tomcat과 Library의  Tmocat을 링크시킴      |
      | 5    | sudo chown -R ### /Library/Tomcat                            | Library의 Tomcat폴더의 권한을 수정 ###에 사용자 이름을 입력  |
      | 6    | sudo chmod +x /Library/Tomcat/bin/*.sh                       | Tomcat의 .sh파일 사용 가능하도록 권한 수정                   |
      | 7    | sudo /Library/Tomcat/bin/startup.sh (sudo /Library/Tomcat/bin/shutdown.sh) | 톰캣 시작 (톰캣 종료)                                        |

   3. 웹 localhost:8080에 접속하여 실행되는지 확인

   4. 따로 시행이 필요는 없으니 종료한 상태로 사용한다.

3. STS3 설치

   1. https://spring.io/tools3/sts/all

   

4. **DB설정(Mac 기준) oracle-xe-11g, SQL Developer 설치**

   1. docker사용

      1. Oracle-xe-11g설치

         |  1   | docker pull deepdiver/docker-oracle-xe-11g                   | deepdiver의 oracle 11g 이미지를 받아옴                       |
         | :--: | ------------------------------------------------------------ | ------------------------------------------------------------ |
         |  2   | docker run -d -p 49160:22 -p 49161:1521 deepdiver/docker-oracle-xe-11g | 이미지를 컨테이너로 생성한 뒤 실행                           |
         | 2-2  | docker run --name <사용자 지정 이름> -d -p 49160:22 -p 49161:1521 -v <디렉토리 경로> deepdiver/docker-oracle-xe-11g | 2는 휘발성으로 재시작하면 사라지므로 사용자 지정 이름을 통해 호출과 저장을 한다. |
   | 2-3  | docker start <사용자 지정 이름>                              | 실행시에는 사용자 지정 이름을 통해 실행을 한다.              |
         |  3   | docker ps                                                    | 컨테이너 목록을 출력                                         |

      2. Sql developer 설치
      
   1. https://www.oracle.com/technetwork/developer-tools/sql-developer/downloads/index.html
         2. 연두 십자를 눌러서 새로운 커넥션 연결
      
         | Name : localhost  |
         | ----------------- |
         | Username : system |
   | Password : oracle |
         | port : 49161      |
         
         3. docker의 oracle 직접 접속방법
            1. docker exe -it <사용자 지정 이름> sqlplus
            2. 비밀번호 변경을 한다.

---

- 시작하기

1. New -> Spring Legacy Project로 새로 생성
2. Spring MVC Project
3. Package 설정
   1. xxx.xxxx.xxx 
4. Servers 설정
   1. servers탭에서 no servers are available. ~ 을 눌러서 설정
   2. apach의 tomcat8.5로 선택
   3. Tomcat 설치 경로를 browse로 선택
      1. /library/tomcat을 경로로 선택 (Mac OS 기준)
         1. /usr/local/tomcat~ 이라고 경로가 되어있음
   4. Finish로 설정 완료
   5. 우클릭으로 서버를 start해준다.
5. 프로젝트를 실행해준다
   1. 프로젝트에서 우클릭 -> run as -> run on server
   2. configure에 서버에 올릴것을 선택 서버 재실행 
6. 준비완료

---

출처

1. https://clearstar0817.tistory.com/9

2. https://clearstar0817.tistory.com/10?category=707475