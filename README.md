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


