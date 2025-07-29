■1. LINUX BASIC
■2. AWS 

_____________________________________________________________________________________________________________________
■1. LINUX BASIC
□1.  실습환경구성
□2.  기본명령어

□1.  실습환경구성
https://learn.microsoft.com/ko-kr/windows/wsl/install-manual

●1) 1단계 - Linux용 Windows 하위 시스템 사용
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

●2) 2단계 - WSL 2 실행에 대한 요구 사항 확인
windows 사양

●3) 3단계 - Virtual Machine 기능 사용
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

●4) 4단계 - Linux 커널 업데이트 패키지 다운로드
●5) 5단계 - WSL 2를 기본 버전으로 설정
wsl --set-default-version 2

●6) 우분투 설치
wsl  -l  -o
wsl  --install  -d  Ubuntu-22.04
wsl  --list  --all             설치확인 

※ 우분투 삭제
wsl  --list  --all  
wsl  --unregister  Ubuntu-22.04
wsl  --shutdown

●7) 중간에 cmd 창
아이디/비밀번호 입력
ubuntu 
ubuntu     비밀번호는 화면상에 안보임
ubuntu     

□2.  기본명령어
●1)   $,  #
```
$  일반 사용자
#  루트 사용자
```

* 루트사용자로 접속
```bash
ubuntu@DESKTOP-ADOR9PH:~$ su -
Password:                                     화면에 안보임  ubuntu
root@DESKTOP-ADOR9PH:~#
```

* root비밀번호 바꾸기
```bash  
PS C:\Users\tj-bu-703-teacher>
PS C:\Users\tj-bu-703-teacher> wsl  -u  root
root@DESKTOP-ADOR9PH:/mnt/c/Users/tj-bu-703-teacher#
root@DESKTOP-ADOR9PH:/mnt/c/Users/tj-bu-703-teacher#
root@DESKTOP-ADOR9PH:/mnt/c/Users/tj-bu-703-teacher# passwd
New password:
Retype new password:
passwd: password updated successfully
root@DESKTOP-ADOR9PH:/mnt/c/Users/tj-bu-703-teacher#
root@DESKTOP-ADOR9PH:/mnt/c/Users/tj-bu-703-teacher#
```

* 파워쉘로 접속
```bash
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.

새로운 크로스 플랫폼 PowerShell 사용 https://aka.ms/pscore6

PS C:\Users\tj-bu-703-teacher> wsl  -d  Ubuntu-22.04  -u  ubuntu
ubuntu@DESKTOP-ADOR9PH:/mnt/c/Users/tj-bu-703-teacher$
ubuntu@DESKTOP-ADOR9PH:/mnt/c/Users/tj-bu-703-teacher$
ubuntu@DESKTOP-ADOR9PH:/mnt/c/Users/tj-bu-703-teacher$ su -
Password:
root@DESKTOP-ADOR9PH:~#
root@DESKTOP-ADOR9PH:~#
```

●2)  명령어 사용법
```bash
명령어  option  input
```
date
cal
   sudo apt update  &&  sudo  apt  install bsdmainutils
cal        2025
cal  05  2025
cal  -y
cal  -j
man   cal

●3)  출력  echo, 위치확인
```
echo   hello  world
echo   $PATH
```
```
which  date
which  echo
```

.........................................................
Q1) 리눅스 열기
Q2) root권한으로 로그인
    ubuntu@User-2023CNVKK:~$   su  -
    비밀번호 
Q3) 현재시스템날짜, 시간 출력  date
Q4) 현재 월 달력 출력   cal
Q5) 현재화면 지우기    clear
Q6) good 출력        echo  good
Q7) echo  명령어 위치확인  which  echo
.........................................................

●4)  디렉토리구조

/          루트
/usr      기본실행
/bin      명령어파일
/etc      설정파일
/home  유저계정
/opt      추가패키지
/tmp     임시파일
/var       시스템운영 로그파일


* 현재 작업디렉토리
```
pwd         
```
* 이동  (change directory)
```bash
cd  
cd  /
cd  ~    계정디렉토리
cd ..      상위디렉토리
```
* 목록확인 
```bash
ls   -al   숨김파일, 상세보기
```


●5)  폴더만들기
```bash
mkdir   폴더명
```
Q basic2 폴더만들고 basic2로 이동
mkdir  basic2  &&  cd  basic2

●6)  파일 쓰고 읽기
쓰고, 추가, 읽기
```bash
cat   >   파일명
cat   >> 파일명 
cat   <   파일명
```
```
pwd
ls  -al
cd   basic2

cat > file1
one
two
three 
^C
```

●7) 파일/폴더복사
``` bash
cp   원본   사본   
```
* 파일복사
```
cp  file1   file2
ls
cat   -n   file2
```
* 폴더복사
```
 cp  -r  basic2  basci4
```

●8) 파일/폴더삭제
```
rm  -r   이름
```

```
rm   file2
```


............................................... QUESTION
Q1. root 로 접속 (pass),    /home/test 폴더만들고 이동 
Q2. 현재위치 확인
Q3. 파일 mynum
one
two
three 내용적기
Q4. 파일읽기
Q5. mynum에 내용추가 - 줄12개
one
two
three 
one
two
three 
one
two
three 
one
two
three 
Q6. mynum에  번호붙이기
Q7. # head  mynum
- 앞에서 10개 데이터만 확인
Q8. # head -n 3 mynum
- 앞에서 3개 데이터만 확인
Q9. # tail    mynum
- 끝에서 10개 데이터만 확인
Q10. # tail  -n 3  mynum 
- 끝에서 3개 데이터만 확인
...............................................


...............................................  ANSWER
Q1. root 로 접속 (pass),    /home/test 폴더만들고 이동 
   su  -
   mkdir  /home/test     &&   cd   /home/test
Q2. 현재위치 확인
   pwd
Q3. 파일 mynum
one
two
three 내용적기

cat  > mynum
ctrl + c

Q4. 파일읽기
cat  mynum

Q5. mynum에 내용추가 - 줄12개   cat >> mynum
one
two
three 
one
two
three 
one
two
three 
one
two
three 
Q6. mynum에  번호붙이기   cat  -n  mynum

Q7. # head  mynum
- 앞에서 10개 데이터만 확인
Q8. # head -n 3 mynum
- 앞에서 3개 데이터만 확인
Q9. # tail    mynum
- 끝에서 10개 데이터만 확인
Q10. # tail  -n 3  mynum 
- 끝에서 3개 데이터만 확인
...............................................


●9) vi editor
- 입력모드(텍스트입력) / 명령모드(커서이동, 복사, 저장)
```bash
파일선택 : vi  파일명
입력모드 : i
빠져나오기 : esc
파일저장     :wq! ( 저장하고 나오기 강제종료)
```
............................................................
Q1.   mynum 파일복사   fruit
Q2.   vi 에디터이용해서 
      one  apple
      two  banana
      three coconut 으로 수정
Q3.  파일 확인
Q4.  test폴더 삭제
............................................................


● 10)  유저권한
#             root
$             일반유저
nologin    System 

1. /home/user1 폴더만들기
2. 유저  user1 
3. 비밀번호설정
4. 유저만들어졌는지 확인
* 유저만들기
```bash
mkdir  /home/user1
useradd  user1  -d /home/user1
passwd   user1
nl  /etc/passwd

grep  /bin/bash   /etc/passwd
```
* 유저로 접근해서 폴더만들기-거부
```bash
su  -  user1
$ mkdir  test
```

* 권한주기
```bash   
            user / group / 기타	
chmod  7        7         7
```
4-read (r)
2-write(w)
1-execute(x)

해석1)
```
chmod  777   모든사용자 r,w,x
chmod  755   사용자 rwx, 그룹 및 기타 rx
```
해석2)
```
chmod  777  /home/user1
chmod  755  /home/user1
chomd  u+x  /home/user1   다른권한안주고 user의 실행권한 추가
```
```
chown   user1:user1   /home/user1   폴더소유자
chmod  755 /home/user1
chmod  u+w  /home/user1    다른권한안건들이고 쓰기권한추가
chmod  u-w  /home/user1    다른권한안건들이고 쓰기권한삭제
```

● 11)  프로세스

```bash
ps  aux   |  grep  ubuntu
```
aux    모든 프로세스 확인


```bash
top
```

```bash
kill -9 PID
```

* bg 백그라운드, fg 포그라운드실행
```bash
sleep  100
ctrl + z
bg
jobs
fg
```

* 터미널 종료해도 프로세스 계속실행
```bash
nohup  프로그램명  &
```


● 12)  압축
```bash
tar  -cvf   my.tar  파일/디렉토리
```
c: 새압축파일생성
v: 진행사항출력
f:  파일이름지정

```
cd /home/ubuntu
 tar  -cvf  my.tar  basci4
```

```bash
tar  -xvf  my.tar
```

_____________________________________________________________________________________________________________________

■2. AWS 
1.  ubuntu  셋팅연습
   1-1  jdk
	◎ 설치할수 있는 jdk 버젼
	sudo  apt-cache  search jdk
	◎ apt 업데이트 
	sudo  apt-get  update
	◎ java 설치
	sudo  apt-get  install  openjdk-11-jdk
	◎ java 버젼확인
	java  -version
	◎ java 경로확인
	which  javac
	readlink  -f  /usr/bin/javac

	/usr/lib/jvm/java-11-openjdk-amd64/bin/javac	

	◎ java 경로설정   /etc/profile
	sudo  vi  /etc/profile
	i
	
	맨끝에
   	export   JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
    	export   PATH=$JAVA_HOME/bin:$PATH
    	export   CLASSPATH=$CLASSPATH:$JAVA_HOME/jre/lib/ext:$JAVA_HOME/lib/tools.jar

	[esc]	
	:wq!

	◎ 경로 설정반영
	source  /etc/profile

	◎ 환경변수 설정확인
	echo   $JAVA_HOME
	echo   $CLASSPATH
	echo   $PATH

   1-2. tomcat9
	◎ 설치할수 있는 tomcat 버젼 
	sudo   apt-cache  search  tomcat

	◎ apt 업데이트  
	sudo  apt-get  update

	◎ tomcat9설치 
	sudo  apt-get  install   tomcat9

	◎ tomcat  버젼확인 
	which  tomcat*
	find   / -name  tomcat*	

	sudo    /usr/share/tomcat9/bin/version.sh

	◎ 방화벽
	sudo ufw  status
	sudo ufw  enable
	sudo ufw  allow  8080/tcp

	sudo ufw  status   |  grep  8080

	◎ 톰캣시작   
	sudo   service    tomcat9   start

	◎ 톰캣시작확인
	sudo   systemctl   status  tomcat9

	◎  ip 확인
	sudo apt-get  install  net-tools
	ifconfig

	......  지우고 다시설치
	......  지우고 다시설치
	sudo rm -rf /etc/tomcat9
	sudo rm -rf /var/lib/tomcat9
	sudo  apt  update
	sudo  apt  install  tomcat9  -y
	sudo  systemctl  start    tomcat9
	sudo  systemctl  status  tomcat9

	localhost:8080

	....... apt-update 에서 멈춘다면
	....... apt-update 에서 멈춘다면
	sudo add-apt-repository universe
	sudo apt update
	


   1-3. mysql
	◎ 설치할수 있는 mysql-server 버젼  
	sudo  apt-cache  search  mysql-server

	◎ apt 업데이트   
	sudo  apt-get  update

	◎ mysql8설치  
	sudo  apt-get  install  mysql-server-8.0

	◎ mysql8버젼확인 
	which  mysql
	find    /  -name   mysql-server-8.0	

	/etc/init.d/mysql  status

	◎ mysql 접속
	sudo  mysql -uroot    비번없음



2.  aws 회원가입
▶▶  STEP0. 회원가입 + 로그인
#1. https://console.aws.amazon.com
   >> 회원가입
#2. 로그인
   >> 루트사용자 


3. aws  ec2 올리기 준비물
1)  만들 프로젝트  배포파일로 만들기     .jar
	1. spring boot     
	2. pom.xml 수정    - lombok 최신
	3. maven  install
2)  filezilla
	https://filezilla-project.org/download.php?platform=win64 
3)  putty     -   key
	https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html
	검색 : rsa	
	- puttygen.exe (a RSA and DSA key generation utility)
	- 64-bit x86: puttygen.exe  다운로드


4. aws  ec2  
https://console.aws.amazon.com
1) 로그인  / 지역설정 - 언어설정
2) ec2 - 대쉬보드   
3) 인스턴스
	- 이름 : myEc2
	- Quick Start : ubuntu   - Ubuntu Server 22.04
  	- 키페어 : Ec2_key  rsa/pem
	- 네트워크설정  : 보안그룹  /   ssh트래픽허용 - 위치무관 0.0.0.0/0
	- 스토리지 구성 : 8Gib
	- 인스턴스개수 : 1

4) jdk11 + tomcat9 + mysq8  설정
4-1) jdk11
	1.  설치할수 있는 jdk 버젼 
		sudo  apt-cache  search jdk
	2.  apt 업데이트
		sudo  apt-get  update
	3.  java 설치  - openjdk-11-jdk
		sudo  apt-get  install openjdk-11-jdk
	4.  java 확인	
		java  -version
	5.  자바경로확인
		which  javac
		readlink   -f  /usr/bin/javac
	6-1.  vi 경로등록
		sudo  vi  /etc/profile	
  		i  
		export   JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
    		export   PATH=$JAVA_HOME/bin:$PATH
    		export   CLASSPATH=$CLASSPATH:$JAVA_HOME/jre/lib/ext:$JAVA_HOME/lib/tools.jar
		esc
		:wq!

	6-2.  nano 설치
		apt-get   install    nano
		sudo  nano  /etc/profile
		맨끝에 경로추가
		ctrl + o
		ctrl + x
	7.  경로반영
		source  /etc/profile
	8.  환경변수 확인   
		echo   $JAVA_HOME
		echo   $PATH
		echo   $CLASSPATH

	※  java  지우기
	sudo  apt-get  remove   --purge openjdk-11-jdk
	sudo  apt-get  autoremove
	sudo  apt-get  clean
	sudo  vi   ~/.bashrc      자바관련지우기
	sudo  source   ~/.bashrc
	java   -version

	※  profile 초기화
	sudo apt-get update
	sudo apt-get install --reinstall base-files

----------------------------------------------------------------------------------------
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "${PS1-}" ]; then
  if [ "${BASH-}" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
  else
    if [ "$(id -u)" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi



        export   JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
        export   PATH=$JAVA_HOME/bin:$PATH
        export   CLASSPATH=$CLASSPATH:$JAVA_HOME/jre/lib/ext:$JAVA_HOME/lib/tools.jar
----------------------------------------------------------------------------------------
 





4-2) tomcat9 
	1.  설치할수 있는 tomcat버젼 
		sudo   apt-cache  search  tomcat
	2.  apt 업데이트
		sudo  apt-get update
	3.  tomcat9 설치  
		sudo  apt-get  install  tomcat9
	
		※ 원하는버젼이 없으면
		tomcat.apache.org   - [tomcat9.0] - [tar.gz]  오른쪽마우스 링크

		cd  /tmp
		wget	https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.104/bin/apache-tomcat-9.0.104.tar.gz
		sudo       mkdir  /opt/tomcat
		sudo       tar      -xvf    /tmp/apach    tab키누르기	    /opt/tomcat/	
		sudo       chown  -R  ubuntu:  /opt/tomcat

	4.  tomcat9 확인	
		sudo  /usr/share/tomcat9/bin/version.sh

		※   /opt/tomcat
		cd    /opt/tomcat/apache-tomcat-9
		./bin/version.sh
			
	5.  방화벽
		sudo  ufw   allow  8080/tcp
	6.  톰캣시작
		sudo   service  tomcat9  start
	7.  톰캣상태확인
		systemctl  status  tomcat9
		ctrl + z  
	8.  ip
		sudo  apt-get  install net-tools
		sudo  netstat  -plnt   | grep  ':8080'
		
		p 프로세스
		ㅣ 현재열려있는 포트만 표시
		n  주소와 포트
		t   tcp만 연결

	9. ec2   8080 포트허용
	[보안그룹]  - 인바운드규칙 - 규칙추가   tcp  8080

	10.  ec2  인스턴스   퍼블릭 ipv4  주소   
		>    주소:8080
		>    54.180.112.15:8080


4-3) mysql
	1.  설치할수 있는 mysql버젼 
		sudo  apt-cache  search   mysql-server 
	2.  apt 업데이트
		sudo  apt-get  update
	3.  mysql설치  - mysql-server8.0
		sudo  apt-get install  mysql-server-8.0
	4.  mysql접속    
		/etc/init.d/mysql  status
		sudo  mysql -uroot         비번없음
	5.  인증확인
		select    user, host, plugin  from   mysql.user;
	6.  인증업데이트
		use mysql
		UPDATE  user  SET  plugin='caching_sha2_password'  WHERE user='root';
		flush  privileges;
	7.  비번바꾸기
		SET password  for   'root'@'localhost'='1234';
	8.  확인
		mysql -uroot -p
		1234

5) putty  키
	1.  ssh   private key
	2. load - all files
	3.  pem  파일선택
	4.  비번체크
	5.  save  private key  - ppk 이름적고 저장
	6.  키설정만들기
	---------------------
	#cloud-config
	ssh_deletekeys: false
	ssh_authorized_keys:       .... 만든키붙이기....
	cloud_final_modules:
 	 - [ssh, always] 
	---------------------

	--------------------- sample
	#cloud-config
	ssh_deletekeys: false
	ssh_authorized_keys:ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCX7YbsS01xz1KG1ohDsYneic3CWRcqmxpW8e3AFnnnoVyEkQtp+1h26SD5+knyM75jNnuMa2hiFEsyFCT6BvFdiOQKwYdksN5kFYrbd9UhgPs4Pg4G2wSBaWA8P82nqQs/zFAsN2sWMDXcOrDJPIK0rBIMMNoaB+oWsgjyaeI59kPcj4HP20JBSC9oUaZi5fYQJcm01XbH8BNiI29Z6Q0SA9wGqYZjHi4aXlD60p+D1VcNERkwYdue5pmAoVur8QgGd92MT3kCC7M0tvn6f7noyu4bJ6oyZ1R9PazfLNiSAGhsAE9ALbc+dkNO+hCdNuv0uIyegjnxDTZJAqxSXWfD imported-openssh-key
	cloud_final_modules:
 	 - [ssh, always] 
	--------------------- sample end

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCX7YbsS01xz1KG1ohDsYneic3CWRcqmxpW8e3AFnnnoVyEkQtp+1h26SD5+knyM75jNnuMa2hiFEsyFCT6BvFdiOQKwYdksN5kFYrbd9UhgPs4Pg4G2wSBaWA8P82nqQs/zFAsN2sWMDXcOrDJPIK0rBIMMNoaB+oWsgjyaeI59kPcj4HP20JBSC9oUaZi5fYQJcm01XbH8BNiI29Z6Q0SA9wGqYZjHi4aXlD60p+D1VcNERkwYdue5pmAoVur8QgGd92MT3kCC7M0tvn6f7noyu4bJ6oyZ1R9PazfLNiSAGhsAE9ALbc+dkNO+hCdNuv0uIyegjnxDTZJAqxSXWfD imported-openssh-key

	7.  ec2에 키설정 붙여넣기 - 인스턴스중지 - 사용자데이터편집 - 인스턴스시작


6) filezilla
	1) file zilla 열기
	2) 사이트관리자열기 - 새사이트 - 이름  myEc2
	[일반] - 프로토콜(SFTP) /  호스트 : 퍼블릭 IPv4 주소
	------------------------------------------------------------
	[로그인유형] - 키파일
	------------------------------------------------------------
	
	3) 접속시   디렉토리가 안나오면
	4) ec2 >  sudo  apt-get update
	5) [ubuntu] - .jar 파일넣기
	6) ec2 >  mysql db만들기 
	7) ec2 >  jar 파일실행
		nohup   java  -jar   파일명.jar  &
		jobs


5.  aws  ec2    관리
1) https 접속
2) 백그라운드로 실행


>> 포트폴리오 올리기
