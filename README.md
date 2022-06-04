# 22-1OSSW

리눅스 top, ps, jobs, kill 명령어
vim 에디터에서 매크로 활용방법 정리

# 목차
+ [1.top](#top)
+ [2.ps](#ps)
+ [3.jobs](#jobs)
+ [4.kill](#kill)
+ [5.매크로 활용방법](#매크로-활용방법)


## top

top 명령어는 현재 OS의 상태를 나타내주는 CLI 어플리케이션이다. 실행 중인 프로세스의 목록을 순서대로 보여주며 일정 간격으로 시스템의 프로세스와 메모리 사용상태를 화면에 출력해준다.

` $ top [option]`
형태로 쓰이고 실행 전 옵션 
 + -b : batch모드
 + -n : 실행 주기 설정
 + -p : 특정 프로세스 ID 
 
 실행 후 명령어
 + shift + m : 메모리 사용량 큰 순서로 정렬
 + shift + t : 실행된 시간 큰 순서로 정렬
 + shift + t : cpu 사용량이 큰 순서로 정렬
 + k         : Process 종료(k 뒤에 종료할 PID 입력)
 + c         : 명령 인자 표시 여부
 + space bar : Refresh
 + q         : 명령어 종료
 + u         : 입력한 유저의 프로세스만 표시
![image](https://user-images.githubusercontent.com/97331187/172019796-87dc2979-00df-4e86-ab88-0faee19dcf53.png)
+ PID : 프로세스 ID
+ USER : 프로세스 사용자 ID
+ PRI : 프로세스 우선순위
+ VIRT : 가상 메모리 사용량


## ps

ps 명령어는 현재 실행중인 프로세스의 목록과 상태를 보여준다.

` $ ps [option]`
형태로 쓰이는데 옵션에 세가지 종류가 있다.
1. Unix Option : 앞에 '-'(dash)가 붙는 옵션 표기방법
2. BSD Option : '-'를 붙이지 않는다.
3. GNU Option : 명령어 앞에 '--'(double dash)를 붙인다.
4. 
표기법이 다르니 정확하게 알고 사용해야한다.

실행 전 옵션
+ -e, -A : 모든 프로세스를 보여준다.
+ -a : 세션 리더와 터미널과 연관된 프로세스들을 제외한 모든 프로세스를 보여준다
+ -f : full format으로 세션의 정보를 표시한다.
+ -ef : -e와 -f의 조합. 모든 프로세스를 full format으로 보여준다.
+ -u userlist : EUID 혹은 유저 이름으로 프로세스를 고른다.
+ -M : 64비트 프로세스들을 보여준다.
+ x : 로그인 상태에 있는 동안 아직 완료되지 않은 프로세서들을 보여준다

![image](https://user-images.githubusercontent.com/97331187/172020534-676b9055-56b7-43f0-9250-b3a465ec9c92.png)
+ UID : 프로세스 소유자의 이름
+ PID : 프로세스의 식별번호
+ PPID : 부모 프로세스 ID
+ C : 짧은 기간 동안의 CPU 사용률
+ STIME : 프로세스가 시작된 시간 혹은 날짜
+ TTY : 프로세스와 연결된 터미널
+ TIME : 총 CPU 사용 시간
+ CMD : 프로세스의 실행 명령행


