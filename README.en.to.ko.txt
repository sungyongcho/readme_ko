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

# Long version

이 문서를 위해서 예시로 연습 모드를 실행 해 보겠습니다. 실제 시험 모드에서는, 당신은 '~/' 에서 시험을 보게 되지만, 연습으로 '~/exam-basedir' 에서 진행하겠습니다.

## 1단계: examshell 시작하기

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

당신이 로그인을 하고, examshell을 통해 어떤 시험을 볼지, 그리고 어떤 레벨에서 시작할지 고르게 됩니다. [미완]

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

## Step 3: Preparing the work directory

확인 이후에, examshell은 working directory를 준비 하고 (연습모드는 `~/exam-basedir/`, 실제 모드는 `~/`), 적당한 Git repository를 선택하고, 등등... 을 할겁니다.

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

## Step 4: Getting an assignment

Examshell will now fetch your current assignment from the system.

It will automatically save the subject in the `subjects` directory. You can read it in a terminal.

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

This display is always accessible using the `status` command.

## Step 5: Work on your assignment

Now, well, you do the work you are assigned.

Note that you HAVE to turn it in in the directory examshell told you, which is a subdirectory of the Git repository with the same name as the assignment. No typos, no anything. If you use the wrong directory, you will fail the assignment, with no option to go back. That'd be bad.

In our example, we would put our `max.c` file in `~/exam-basedir/rendu/max/`.

You WILL have to push your work after you're done, as with any regular project, so don't forget !

## Step 6: Request to be graded

Once you're SURE that your work is done correctly, and that you have pushed it to vogsphere, you can use the `grademe` command to request that your assignment be graded:

```
examshell> grademe

Before continuing, please make ABSOLUTELY SURE that you have pushed your files,
that they are in the right directory, that you didn't forget anything, etc...
If your assignment is wrong, you will have another assignment at the same level,
but with less potential points to earn!

Are you sure? [y/N]
```

So, yeah, let's say we're sure.

```
[...]

Are you sure? [y/N] y
OK, making grading request to server now.

We will now wait for the job to complete.
Please be patient, this CAN take several minutes...
(10 seconds is fast, 30 seconds is expected, 3 minutes is a maximum)
waiting...
```

Now we wait for the system to grade us. It actually CAN take some time, but that's expected, so don't panic unless you wait for 1-2 minutes, in which case you should just ask a staff member, it's an easy fix.

### Success !

```
[...]
waiting...
>>>>>>>>>> SUCCESS <<<<<<<<<<
You have successfully completed the assignment and earned 16 points!
Trace saved to ~/exam-basedir/traces/0-0_max.trace

(Press Enter to continue...)
```

In this case, we succeeded. The grading trace is automatically saved for us to read if we want.

The next status message will show that:

* We earned the points in play for the assignment (16)
* We have gone up a level (now at 1)
* We have a new assignment

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

If that had been the last level of the exam, examshell would have said it, and told us the exam was finished.

### Failure :(

Let's fail this one, just to see what it does:

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

In this case, we failed, so :

* We do NOT get the points
* We do NOT go up a level (we stay at 1)
* We get a new assignment, but with 5 less points to gain !

If that had been the last possible assignment in this level, examshell would have said it, and told us the exam was finished.

### Error :<

There is the possibility that examshell says the grading resulted in an ERROR. This does not mean you failed, it means that
the grading system itself has failed.

However, don't panic !

You will have the option to either retry or abort. You SHOULD retry at least once, because errors in the grading system are rare,
and usually transient, so they'd resolve with a retry. If a retry does not solve the error, get a staff member to help !

If all else fails, then you can abort. This would give you another assignment of the same level, but without losing potential
points.

## Step 7: Let's go again

That's basically it. You will continue getting new assignments until either you fail enough assignments to exhaust a level's pool of assignments, or you succeed at the last level of the exam.

If you want, you can end your session at any time by using the `finish` command.

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

## Examshell tells me "Mismatched versions", what gives ?

The machine you are on is probably just not updated yet. Either switch to another computer, or come to the Bocal and ask us to update it.

## Why can't I use real mode // practice mode ?

Examshell tells you exactly why. Here are the possible reasons:

* "Can't practice when logged in as 'exam'"
	* You have to login using your regular session to use practice mode
* "Project doesn't allow it"
	* This means the exam project in itself forbids using a specific mode. You can't do anything about that.
* "You must subscribe to an exam event"
	* As said in the introduction, to do the exam in real mode, you have to be subscribed to an exam session on the intranet. You can do that in your calendar.
* "You must retry the project on the intranet"
	* You can not use real mode if you haven't retried the project on the intranet, because the system wouldn't be able to give you a grade for it.
* "Current event doesn't allow for this exam"
	* Some exams are restricted to specific sessions. Most notably during a "piscine". You will have to attend a session that's made specifically for this exam
* "Can't do it from this location"
	* Most exams are restricted to a specific location so that the exam is done under controlled conditions. You have to login at one of these places ! Practice mode, however, is available from anywhere
* "Too early, well be OK in XXX" // "Too late, ended at XXX"
	* Means the closest exam session you are subscribed to is not yet started or has already ended.
* "Must login as 'exam' to run in real mode"
	* Pretty self-explanatory, isn't it ? Just login as "exam" with password "exam".

## 전 제 동료와 똑같은 과제를 받지 못했나요, 너무 불공평해요!

네. 안됐네요. 받아들이세요.

## Can I access my repository after the exam ? What about the subjects ?

Normally, you'll get an email with all of this after the exam is marked as finished.

If you didn't ... well, wait. If you really don't receive it, too bad, life is unfair I guess.

## Examshell 이 저 실패 했다고 하는데, 전 맹세하는데 진짜로 아니에요!

대부분, 당신은 이런 걸 까먹었을 겁니다 :

* push 하셨나요?
* 진짜로 ?
* 올바른 directory를 사용 했나요? Did you use the right directory ?
* 당신의 파일 이름 전부다 정확 한가요 ?
* 당신 진짜로 맞는 과제를 한게 맞죠 ?
* 당신 찐으로 push 했나요 ?
* 기타등등 ...

If you are really, really, REALLY, ABSOLUTELY sure you have done it right, and that the system fucked you, well, just come tell the staff AFTER THE EXAM. We will look at it, but please, please, please think before you come see us : It really is most likely it's your fault, and it takes us a long time to try to look for an error in the assignment itself.

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
