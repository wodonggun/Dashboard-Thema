
## ETRI Dashboard 정리

## 환경 설정 (ubuntu 16.04, tomcat 8, mptcp 커널로 부팅)
* Tomcat
  * <https://wnsgml972.github.io/linux/linux_ubuntu_tomcat.html>
* JSP
  * <https://wnsgml972.github.io/linux/linux_jsp.html>
* ffserver conf 를 이용한 ffserver 실행
  * 설치 <https://wnsgml972.github.io/ffmpeg/ffmpeg_ffserver_config.html>
  * 사용법 <https://wnsgml972.github.io/ffmpeg/ffmpeg_ffserver_streamming.html>
* VM Adapter (5개 이상의 어뎁터 생성)
  * <https://github.com/wnsgml972/Dashboard-Thema/blob/etri/in_vm_create_more_than_5_adaters.md>
* localhost Interface 설정
  * <https://github.com/wnsgml972/Dashboard-Thema/blob/etri/localhost.md>
* IpSec
  * <https://github.com/wnsgml972/Dashboard-Thema/blob/etri/ipsec.md>
* GRE Tunnel
  * <https://github.com/wnsgml972/Dashboard-Thema/blob/etri/gre.md>

## clone시 할 것 (user로 로그인 하면 편함!)
  1. /dashboard/conf/ffserver.conf의 ACL allow에 스트리밍 서버를 올릴 ip 추가  [conf 파일 변경]
  2. /dashboard/WebContent/jsp/* 파일들의 실행 path 모두 변경 [user로 로그인 시 필요 없음]
  4. wget 사용을 위해 상대방 컴퓨터의 ROOT에 file1 ~ file4 올려놓기
  5. ipsec-sh 디렉토리의 path 변경 [user로 로그인 시 필요 없음]

## 키워드 [ 조절 ]
* 프로그래밍 시 url path나 chart를 수정

<hr/>

### HTML
* index.html  
* index2.html  
* index3.html  
* system.html (추 후)

### Directory
* jsp
  * process build bath 조절
* conf
  * ffserver.conf  
  * VM local 환경에서 네트워크 대역폭 한계 설정 명령어 모음, 수신량만 조절 가능, 송신량은 조절 불가
* etri-jsp-sh
  * 쉘 스크립트 모음
  * ifdown ifup, 원하는 인터페이스 down 또는 up 조절
  * play-ffmpeg, input url 조절
  * bw.sh 네트워크 대역폭 1초마다 계속,  bw1.sh 네트워크 대역폭 한번
  * <https://github.com/wnsgml972/Dashboard-Thema/blob/etri/bandwidth.md>
* ipsec-sh
  * 쉘 스크립트 모음
  * wget, capture 프로그램이 있음
* system-cpp-sh
  * 시스템 관리 cpp + 쉘 스크립트 모음
  * <https://github.com/wnsgml972/Dashboard-Thema/blob/etri/system.md>

### Java Script
* build/js/custom.min.js
  * junhee code (제일 위, 제일 아래)
  * lineChart 검색( 여기서 네트워크 대역폭 차트 조절 )
* build/js/custom.jun.js  
  * 커스텀 자바 스크립트

### Flow
* 버튼 클릭 시
  1. jsp 코드 호출
  2. jsp 코드 내에서 프로세스 빌더를 이용해 쉘 스크립트 실행
  3. 결과를 ajax로 가져와 실행
* onload시 1초마다 쉘 스크립트를 실행하여 네트워크 대역폭을 line chart에 대입
* JSP를 이용한 쉘 스크립트 실행 <https://wnsgml972.github.io/linux/linux_shellscript.html>
