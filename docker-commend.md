// 도커 이미지 pull 받아오기 (httpd)
$ docker pull httpd

// 이미지 잘 받아와졌는지 확인하기
$ docker images

// index.html 만들기
$ echo "Hello World" > index.html

// 홈에 있는 test 폴더를 마운트 시킬것임
$ docker run -p 8888:80 -v ~/test:/usr/local/apache2/htdocs httpd

// 현재 실행중인 도커 컨테이너 보기
$ docker ps

// 나온 컨테이너 id 로 exec 한다 (/bin/sh는 exec 명령어로 접속시 사용하는 로그인쉘을 지정하는 명령어)
// exec 도커 컨테이너의 터미널로 접속하기
$ docker exec -it {{컨테이너ID}} /bin/sh

// 도커 파일 만들기
$ echo "FROM httpd:latest
COPY index.html /usr/local/apache2/htdocs/index.html
EXPOSE 80" > Dockerfile

// 도커 이미지 만들기
$ docker build -t my-httpd .

// 도커 이미지 만들어졌는지 확인하기
$ docker images

// 빌드한 이미지 실행하기
// 로컬 컴퓨터의 8888번 포트를 도커컨테이너의 80번 포트로 연결한다
$ docker run -p 8888:80 my-httpd

