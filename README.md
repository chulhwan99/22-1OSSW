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


## jobs

jobs 명령어는 작업의 상태를 표시하는 명령어다. 현재 쉘 세션에서 실행시킨 백그라운드 작업의 목록이 출력되며, 각 직업에는 번호가 붙어 있어 kill 명령어 뒤에 '%번호' 등으로 사용할 수 있다.
` jobs [option][job ID] `

실행 전 옵션
+ -l : 프로세스 그룹 ID를 state 필드 앞에 출력
+ -n : 프로세스 그룹 중에서 대표 프로세스 ID를 출력
+ -p : 각 프로세스 ID에 대해 한 행씩 출력
+ command : 지정한 명령어를 실행

jobs로 알 수 있는 백그라운드 작업의 상태값
+ Running : 작업이 계속 진행중 
+ Done : 작업이 완료되어 0을 반환
+ Done(code) : 작업이 종료되었으며 0이 아닌 코드를 반환
+ Stopped : 작업이 일시 중단
+ Stopped(SIGTSTP) : SIGTSTP 시그널이 작업을 일시 중단
+ Stopped(SIGSTOP) : SIGSTOP 시그널이 작업을 일시 중단
+ Stopped(SIGTTIN) : SIGTTIN 시그널이 작업을 일시 중단
+ Stopped(SIGTTOU) : SIGTTOU 시그널이 작업을 일시 중단


## kill

kill 명령어는 이름 처럼 프로세스를 죽일 때 사용한다. 강제로 종료하는 명령어는 아니고 프로세스에 시그널을 보내는명령어다. default 시그널은 TERM(15)다.
` kill [pid]` 형태로 ps 명령어를 통해 얻은 pid를 kill 명령어의 파라미터로 넘겨 실행시킨다.
시그널을 바꾸고 싶다면 ` kill -(signal) [pid] `  
![image](https://user-images.githubusercontent.com/97331187/172031572-32b840b7-81e2-4341-a92d-831e8553a4d5.png)
`kill -l` 로 시그널의 리스트를 출력한 모습이다.

되도록 9번 시그널 SIGKILL은 사용하지 않는 것이 좋다. SIGTERM의 경우 종료 시그널에 대해 시그널 핸들러를 등록하여 처리 중이던 데이터를 안전하게 정리/보관하는데, SIGKILL은 프로세스를 강제로 종료하는 방식이기 때문이다.





