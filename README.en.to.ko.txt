# 서론

이 시험 시스템은 하나하나씩 과제가 주어 지고, 당신이 요청 할 때 채점이 진행됩니다.

하나의 시험은 레벨들의 세트로 주어지고, 각 레벨은 가능 한 과제의 모음들 중에서 한가지의 과제가 무작위로 주어질 것입니다. 아마 당신의 동료가 당신과 동일한 과제가 주어지지 않을 것입니다. 삶은 불공평 하니, 받아들이세요.

각 레벨을 통과 하게되면, 당신은 점수를 받게 되고, 총점은 100점이 됩니다.

## 시험 이전

시험을 치르기 전에, 당신은 인트라넷에서 적어도 한 시험 프로젝트에 시험에 구독(subscribe)된 상타여야 합니다. 당신이 원하는 만큼 시험에 구독 할 수있고, 여기에는 제한이 없습니다.

당신이 시험에 적어도 하나 이상의 시험 프로젝트에 구독 되어있다면, 당신은 'examshell' 을 통하여 시험에 접근 할 수 있지만, '연습 모드' 로만 접근이 가능합니다.

당신이 실제로 시험에 접속 하고 싶다면, exam session에도 구독이 되어 있어야 합니다. 시험시간을 꼭 지키고, 시험장에 "exam"으로 로그인 합니다. 이렇게 하여야만 당신은 실제 모드로 시험을 볼 수 있습니다.

## 시험 모드

두 가지의 시험 모드가 있습니다.There are two exam modes :

* 연습 모드는, 당신이 원하는 시간에 언제 어디서든간에 세션에 접속 할 수 있습니다. 연습 모드는 모든것이 보통처럼 작동하지만, 인트라넷에 성적이 등록 되진 않습니다. 시험은 언제든지 원하는 만큼 연습 해 볼 수 있습니다.
* 실제 모드는, "exam" 세션에만 접속 할 수 있는 모드로써, 시험장에서, 시험 이벤트가 있을 때만 접속 가능합니다. 이 모드에서는, 당신의 시험 점수가 인트라넷에 등록되고, 당신이 시험 세션을 종료 하면 시험 점수가 결정되게 됩니다.

## Examshell

당신은 'examshell'이라는 프로그램을 통해 시험 시스템과 마주하게 됩니다.

당신은 시험 시작 후 10분 안에 시험이 시작된 이후에 각자의 터미널위에서 시험을 시작 해야만 합니다. 만약 당신이 실수로 그만두었다면, 문제 될게 없고, 터미널 위에 'examshell'을 입력 하여 시험을 재개 하면 됩니다. 이렇게 하면 이전부터 과정이 다시 시작됩니다.

# 짧은 버전 (기존 번역본 활용 하면 될것 같습니다)

1. You start examshell
2. Examshell tells you the different exams you have access to
3. You choose an exam and a starting level
4. The system creates a Git repository for you and clones is to BASEDIR/rendu
5. The system chooses a random assignment for you in the current level
6. Examshell downloads the subject for the assignements to BASEDIR/subjects/ASSIGNMENT_NAME/
7. Examshell tells you what assignment you're supposed to do, how many points you stand to win, and where you should turn it in
8. You work on your assignment
9. You push your assignment on the Git repository as usual
10. You are sure you're finished: You tell examshell to grade you using the `grademe` command
11. The system grades your assignment
12. Examshell saves the grading trace to BASEDIR/traces/ASSIGNMENT_TRACE_DIR
13. If you succeeded, you will gain points and go up one level. If there are levels left in the exam, goto 5, else the exam is finished
14. If you failed, you stay at the same level, lose 5 potential points, and goto 5. If there are no more assignments in the current level's pool, the exam is finished.

무슨 말인지 모르겠다구요? 긴 버전을 읽으세요!

# 긴 버전

이 문서를 위해서 예시로 연습 모드를 실행 해 보겠습니다. 실제 시험 모드에서는, 당신은 '~/' 에서 시험을 보게 되지만, 연습으로 '~/exam-basedir' 에서 진행하겠습니다.

## 1단계 : examshell 시작하기

```
zaz@blackjack ~ $ examshell
examshell v0.1.1

WARNING
Your exam files will be stored in ~/exam-basedir
THIS DIRECTORY WILL BE ENTIRELY EMPTIED BEFORE YOU START
So, if you do have important things there, Ctrl-C NOW and back them up before running this.
(Press Enter to continue...)
```

이 경고문은 매우 평범한것입니다. 이는 단지 당신이 '~/exam-basedir/' 위에 무언가 중요한 자료가 남아 있지 않는것을 확인 하는것이고, 왜냐하면 examshell이 완전히 비워버릴 것이기 때문입니다. 이렇게 하면 우리는 "깨끗한" 시험을 볼 경로를 가지게 됩니다.

만약 실제 모드였다면, 경고문은 출력되지 않을것입니다.

## 2단계 : 시험 고르기

당신이 로그인을 하고, examshell을 통해 어떤 시험을 볼지, 그리고 어떤 레벨에서 시작할지 고르게 됩니다. 당신은 이 시험에서 한번 확인된 레벨에서만 시험을 시작 할 수 있습니다. (애매합니다))

```
[...]
Getting current exam session from server...

The following projects are available to you at the moment:

  0 : Exam C
      Maximum start level    : 4 (Best grade you got is 75)
      Real mode available    : no (You must subscribe to an exam event)
      Practice mode available: yes (Ends in 4 hours, 0 minutes and 0 seconds)

There is only one project you can do right now.
Automatically selecting project 0: "Exam C"

This project can only be done in practice mode
In 'practice' mode, your grade will not be taken into account, and you can only access your repository from your regular (non-exam) session

Please select the level at which you would like to start your session
Be aware that if you select a level higher than 0, you will only gain however many points the previous levels would have given you IF you complete your selected starting level !

Desired start level (0-4):
```

만약 여기서 하나 이상의 시험이 있다면, 당연히 당신은 하나만 고를겁니다.

이 예시에서는, 우리는 레벨 0에서 시작할게요. 만약 이 시험이 어떤 레벨에서 시작할지 물어보지 않는다면, 당황하지 마시고, 그뜻은 당신이 선택한 시험이 레벨 0 말고 다른 레벨에서 시험을 시작 할 수 없다는 이야기입니다.

```
[...]
Desired start level (0-4): 0

You are about to start the project "Exam C", in practice mode, at level 0.
You would have 4 hours, 0 minutes and 0 seconds to complete this project
Confirm ? [y/n]
```

만약에 당신이 어떤 이유로든 지금 뭘 하는건지 확신이 안들면, 'n'을 입력하면 다시 선택할 수 있습니다.

만약 당신이 어떤 이유로든 프로젝트를 선택한 이후로 examshell을 재새작 해야된다면, 당연히 다시 선택하라고 물어보지 않을겁니다. 바로 step 3로 넘어가게 됩니다.

## 3단계 : 작업용 디렉토리 준비하기

확인 이후에, examshell은 작업용 디렉토리를 준비 하고 (연습모드는 `~/exam-basedir/`, 실제 모드는 `~/`), 적당한 Git repository를 선택하고, 등등... 을 할겁니다.

```
[...]
Confirm ? [y/n] y
Selecting project...
Creating required directories...
Ensuring your Git repository for this exam is present and correct...
Git repository is not cloned yet. Cloning...
Cloning into '/Users/zaz/exam-basedir/rendu'...
vogsphere: (INFO) Transaction ID : 8ed938b3-fe1e-4eb6-b561-0f6622e12b82
vogsphere: (INFO) Please mention this ID in any ticket you create concerning this transaction
vogsphere: (INFO) This transaction has been started at 2015-05-28 11:07:49, server time.
vogsphere: (INFO) Rights will be determined using this time, so do NOT cut the connection.
vogsphere: (INFO) It appears you are mmontinet. If that's not true, check your Kerberos tickets (klist)
vogsphere: (INFO) You have read and write rights on this repository
warning: You appear to have cloned an empty repository.

Your git repository was successfully cloned to ~/exam-basedir/rendu

The following commands are available to you:
  status: Displays the status of your session, including information about
    your current assignment, and the exam history.
  grademe: Asks the server to grade your current assignment. If you
    have done it right, you will gain the points of the current assignment, go
    up a level, and try the next one. If you fail, however, you will have
    another assignment of the same level to do, and it will potentially bring
    you less points on your grade ... So be sure of yourself before you launch
    this command !
  finish: Tells the server you are finished with your exam.

You can log out at any time. If this program tells you you earned points,
then they will be counted whatever happens.

(Press Enter to continue...)
```

## 3단계 : 문제 받아오기

Examshell 은 이제 현재 당신이 풀 과제를 시스템에서 가져올겁니다.

자동으로 문제를 'subjects' 디렉토리에 저장 할것입니다. 터미널에서 읽읅 수 있습니다.

```
[...]
================================================================================
You are currently at level 0
You are running in practice mode (Your grade does not count)
Your current grade is 0/100
Assignments:
  Level 0:
    0: max for 16 potential points (Current)

Your current assignment is max for 16 potential points
It is assignment 0 for level 0
The subject is located at: ~/exam-basedir/subjects/max
You must turn in your files in a subdirectory of your Git repository with the
same name as the assignment (~/exam-basedir/rendu/max).
Of course, you must still push...

The end date for this exam is: 28/05/2015 15:07:47
You have 3 hours, 54 minutes and 11 seconds remaining
================================================================================
You can now work on your assignment. When you are sure you're done with it,
push it to vogsphere, and then use the "grademe" command to be graded.
examshell>
```

이 화면은 'status' 명령어를 사용하여 언제든 접근이 가능합니다.

## 5단계 : 문제 풀기

자 이제, 당신은 지정 받은 문제를 풀면 됩니다.

유의 하여야 할 점으로 examshell이 제출 하라고 명시한 디렉토리 안에 꼭 제출 하셔야 합니다. Git 저장소의 서브 디렉토리로써 문제의 이름과 같아야합니다. 오타 없이, 다른 아무것도 없이요. 만약 틀린 경로를 사용하게되면, 당신은 문제를 틀리게 되고, 다시 돌아갈 수 있는 방법이 없습니다. 그럼 안좋겠죠.


이번 예제에서, 우리는`~/exam-basedir/rendu/max/` 경로 내에 `max.c` 파일을 집어 넣겠습니다.

당신은 답안 작성 완료 후에 다른 프로젝트들 처럼 push 를 해야하니, 까먹지마세요!

## 6단계 : 채점 요청하기

당신이 문제를 잘 풀었다는것을 확신하고, vogsphere로 push 를 완료 했다면, `grademe` 를 사용하여 당신이 푼 문제의 채점을 요청 할 수 있습니다:

```
examshell> grademe

Before continuing, please make ABSOLUTELY SURE that you have pushed your files,
that they are in the right directory, that you didn't forget anything, etc...
If your assignment is wrong, you will have another assignment at the same level,
but with less potential points to earn!

Are you sure? [y/N]
```

음, 그래요, 확신한다고 해봅시다.

```
[...]

Are you sure? [y/N] y
OK, making grading request to server now.

We will now wait for the job to complete.
Please be patient, this CAN take several minutes...
(10 seconds is fast, 30 seconds is expected, 3 minutes is a maximum)
waiting...
```

이제 우리는 시스템이 채점하기를 기다립니다. 이 과정에 약간의 시간이 들 수도 있는데, 원래 이런거니까, 1-2분 넘게 기다린게 아니면 침착하시고, 만약 그렇다면 그냥 스태프에게 말씀하세요, 금방 고쳐드릴테니까요.

### 성공 !

```
[...]
waiting...
>>>>>>>>>> SUCCESS <<<<<<<<<<
You have successfully completed the assignment and earned 16 points!
Trace saved to ~/exam-basedir/traces/0-0_max.trace

(Press Enter to continue...)
```

이 상황에서는, 성공했네요. 이 채점 기록은 우리가 만약 원한다면 읽(을수 있)도록 자동으로 저장됩니다.

다음 상태 메세지는 아래의 것을 보여줄겁니다:

* 우리는 과제를 수행 한것에 대한 점수를 얻게 되었다. (16)
* 우리는 레벨이 상승하게 되었다 (이제 1로)
* 우리는 새로운 과제를 얻게 되었다.

```
[...]
(Press Enter to continue...)

================================================================================
You are currently at level 1
You are running in practice mode (Your grade does not count)
Your current grade is 16/100
Assignments:
  Level 0:
    0: max for 16 potential points (Success)
  Level 1:
    0: wdmatch for 16 potential points (Current)

Your current assignment is wdmatch for 16 potential points
It is assignment 0 for level 1
The subject is located at: ~/exam-basedir/subjects/wdmatch
You must turn in your files in a subdirectory of your Git repository with the
same name as the assignment (~/exam-basedir/rendu/wdmatch).
Of course, you must still push...

The end date for this exam is: 28/05/2015 15:07:47
You have 3 hours, 42 minutes and 27 seconds remaining
================================================================================
You can now work on your assignment. When you are sure you're done with it,
push it to vogsphere, and then use the "grademe" command to be graded.
examshell>
```

아마 저 레벨이 시험의 마지막 레벨이라면, examshell은 당신과 우리에게 시험이 완료되었다고 알릴것입니다.

### 실패 :(

이번 문제를 실패해서, 어떤 상황이 벌어지는지 확인을 해봅시다:

```
[...]
examshell> grademe

Before continuing, please make ABSOLUTELY SURE that you have pushed your files,
that they are in the right directory, that you didn't forget anything, etc...
If your assignment is wrong, you will have another assignment at the same level,
but with less potential points to earn!

Are you sure? [y/N] y
OK, making grading request to server now.

We will now wait for the job to complete.
Please be patient, this CAN take several minutes...
(10 seconds is fast, 30 seconds is expected, 3 minutes is a maximum)
waiting...
>>>>>>>>>> FAILURE <<<<<<<<<<
You have failed the assignment.
Trace saved to ~/exam-basedir/traces/1-0_wdmatch.trace

(Press Enter to continue...)

================================================================================
You are currently at level 1
You are running in practice mode (Your grade does not count)
Your current grade is 16/100
Assignments:
  Level 0:
    0: max for 16 potential points (Success)
  Level 1:
    0: wdmatch for 16 potential points (Failure)
    1: ft_strrev for 11 potential points (Current)

Your current assignment is ft_strrev for 11 potential points
It is assignment 1 for level 1
The subject is located at: ~/exam-basedir/subjects/ft_strrev
You must turn in your files in a subdirectory of your Git repository with the
same name as the assignment (~/exam-basedir/rendu/ft_strrev).
Of course, you must still push...

The end date for this exam is: 28/05/2015 15:07:47
You have 3 hours, 41 minutes and 25 seconds remaining
================================================================================
You can now work on your assignment. When you are sure you're done with it,
push it to vogsphere, and then use the "grademe" command to be graded.
examshell>
```

이 상황에서, 우리는 실패를 했기 때문에:

* 우리는 점수를 받지 않게 된다
* 우리의 레벨은 상승하지 않게 된다 (1에 남아 있음)
* 우리는 새로운 문제를 받게 되지만, 획득 가능 점수가 5점 줄어들어있다 !

이 문제가 지금 레벨에서 풀수있는 마지막 문제였다면, examshell은 당신과 우리에게 시험이 종료되었다고 알릴것입니다.

### 에러 :<

아마 examshell 이 채점의 결과가 ERROR라고 알려줄 가능성이 있습니다. 이 뜻은 당신이 문제를 틀렸다는 것이 아니라,
시스템이 채점에 실패했다는 뜻입니다.

그러나, 침착하세요!

당신은 재시도 하거나 무시 할 옵션이 있을겁니다. 적어도 꼭 한번은 재시도를 해보세요, 이런 에러는 흔한 경우가 아니고,
보통 일시적인 현상이기 때문에, 재시도를 통해서 문제가 해결 될겁니다. 만약 재시도를 했는데 에러가 해결되지 않는다면, 스태프 멤버를 찾아 도움을 요청하세요 !

만약 전부 해결이 안되면, 그냥 무시를 선택할 수 있습니다. 이는 당신에게 같은 레벨에서 다른 문제를 줄거고, 읽게되는 점수가 없는 상태일것입니다.

## 7단계 : 다시 해봅시다

이게 전부입니다. 당신은 새로운 질문의 풀의 범위가 다 떨어질 때 까지 새로운 문제들을 받아 시험에 낙제하거나, 시험에서 마지막 레벨에 도달하게 되어 시험을 성공하게 될것입니다.

원하신다면, 'finish' 명령어를 사용하여 당신의 세션을 언제든지 종료할 수 있습니다.

```
examshell> finish
Please confirm that you REALLY want to end your current session.
If you do, you will not be able to do anything with it anymore!
Are you finished? [y/N] y
Your session has been marked as finished. You may now log out.
zaz@blackjack ~ $
```

# FAQ / 일반적인 오류들

## 저 examshell을 멈춰버렸어요, 어떻게 하나요?

그냥 다시 사작하세요, 별일 아닙니다.

## Examshell 이 "login window expired" 라고 하는데, 뭘 해야되나요 ?

당신은 시험 이 시작된 후 10분 안에 시험을 골라야하고, 이후로는 이 에러가 나올텐데 간단히 말해서 너무 늦었다는 말입니다.
안되요, 아무것도 할 수가 없어요.

## Examshell 이"Mismatched versions" 이라는데, 뭘 해야하나요 ?

당신이 앉아있는 컴퓨터가 업데이트 되어있지 않았다는 뜻일겁니다. 다른 컴퓨터에 가서 앉거나, Bocal에게 가서 업데이트를 요청하세요.

## 왜 저는 real mode나// practice mode 를 사용할 수 없는건가요 ?

Examshell 은 당신에게 정확하게 이야기 말할거고, 다음 이유들에서 이기 때문입니다:

* "Can't practice when logged in as 'exam'"
	* 당신은 연습 모드를 사용하려면 보통 세션에서 로그인 되어 있어야합니다.
* "Project doesn't allow it"
	* 이 말은 이 시험 프로젝트가 특정 모드에 막혀있다는 뜻입니다. 당신은 아무것도 할수 없어요.
* "You must subscribe to an exam event"
	* 앞전에도 이야기 한것처럼, 실제 모드에서 시험을 보려면, intranet 상에서 시험 세션에 구독 한 상태여야 합니다. Calenar 위에서 가능해요.
* "You must retry the project on the intranet"
	* 당신은 intranet 위에서 재시도 하지 않았으면 실제 모드를 이용 할 수 없습니다. 왜냐하면 시스템이 당신에게 점수를 매길 수 없기 때문입니다.
* "Current event doesn't allow for this exam"
	* 몇몇 시험들은 특정 세션에 제한되어 있습니다. 대부분이 "piscine"의 경우 입니다. 당신은 이 모드를 실행 할수 있는 시험에 참여 하여야 합니다.
* "Can't do it from this location"
	* 대부분의 시험은 특정 지역에서 제한되어 있기 때문에 통제된 사함에서 시험이 치뤄지게 됩니다. 당신은 특정 장소에 가서 로그인 해야합니다! 연습모드는, 그러나, 어디서든 가능합니다
* "Too early, well be OK in XXX" // "Too late, ended at XXX"
	* 이말은 당신이 등록한 시험 세션이 아직 시작 안했다거나, 이미 종료되었다는 소리입니다.
* "Must login as 'exam' to run in real mode"
	* 말 그대로 설명하고 있는데, 그렇지 않나요? 그냥 "exam"으로, 비밀번호 "exam"으로 로그인하세요.

## 전 제 동료와 똑같은 과제를 받지 못했나요, 너무 불공평해요!

네. 안됐네요. 받아들이세요.

## 시험 이후에 저장소에 접근이 가능한가요? 과제들은요 ?

보통은 , 시험 종료후에 이 모둔것에 대해 시험이 종료되었다고 표시된 후에 이메일을 받게 될겁니다.

만약 안그랬다면 ... 음, 기다리세요. 만약 진짜로 못받았으면, 안됐네요, 삶이 불공평한거라서.

## Examshell 이 저 실패 했다고 하는데, 전 맹세하는데 진짜로 아니에요!

대부분, 당신은 이런 걸 까먹었을 겁니다 :

* push 하셨나요?
* 진짜로 ?
* 올바른 directory를 사용 했나요? Did you use the right directory ?
* 당신의 파일 이름 전부다 정확 한가요 ?
* 당신 진짜로 맞는 과제를 한게 맞죠 ?
* 당신 찐으로 push 했나요 ?
* 기타등등 ...

만약 당신이 진짜, 진짜, 진심으로, 완전히 문제를 잘 풀었다고 확신하고, 시스템이 너 좆되봐라 한것같으면, 그냥 시험 후에 스태프에게 오세요. 한번 볼텐데, 제발, 제발, 젭알 한번 오기 전에 생각 해보고 오세요: 진짜 대부분은 당신이 잘못한거고,이 시험문제가 잘못 되었다는것을 알아보려면 저희에겐 긴 시간이 걸립니다.

## 니네 시스템 썩었고, 전 예전 시스템을 원해요!

아뇨 안그렇구요, 그리고 안되요 예전걸로 다시 못돌아가요.

## 제가 시스템에서 버그를 찾았어요!

진짜로 ?

음, 당신이 찾았으면, 저희에게 알려주세요. 부정행위를 하지 않으면, 저희는 당신에게 화나지 않을겁니다.

## 제가 시스템에서 버그를 찾았고, 시험에서 개이득 했는데, 님들은 절대로 절 못잡을거에요!

네 잡을거에요. 언젠가는! 그리고 우리는 당신이 다른 학교를 찾아 보는것을 즐기는걸 바랄게요 :)

장난아니고, 멍청하게 굴지 마시고, 그냥 제보 하시고 넘어가세요. 시험 점수 몇점 때문에 짤리는건 별 소득이 없잖아요, 그렇죠?

## Examshell 이 project 를 선택하는데 제가 너무 오래 기다렸다고 하는데, 어쩌죠?

잘못된거 하나도 없으니까, 다시 시도하세요. 이건 에러가 아니라, 당신이 너무 결정장애가 있다고 하는 examshell의 모냥 빠지는 방법으로 알리는 것입니다.. (번역이 참 어렵네요..)

## 시험 채점 요청을 보냈는데 시간이 오래 걸려요.

음, 그게 어떤 시점에서 끝나기는 하나요? 오래 기다려도, 한 1~2분 정도 후에, 끝나지 않으면, 스태프 멤버에가 가세요. 왜냐하면 이건 보통 흔한건 아닌데, 저희는 쉽게 고칠수 있어요.

# 왜 '연습 모드'는 시험 세션에서 금지 된건가요?

내가 그렇다고 하면 그런거니까.

## 저는 이 FAQ에 답변이 없는 질문을 가지고 있는데, 이 FAQ 정말 쓸모없네요!

잘됬네요. 그냥 저희에게 와서 물어 보시면 추가 할텐데, 아무래도 어떤 약물 도움 없이는 모든걸 생각 해낼수가 없네요.
