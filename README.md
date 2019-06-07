# Git
for my use

기본 command line 명령어

mkdir filename
cd filename
cd ..
rm -rf filename
ls 
ls -al
cat filename (to see the file content)
vim filename (create a file / i : insert / :wq : write and quit)


Git 명령어

git 명령어 —-help

git init
 - .git 파일을 만들어서 git initialize 해 줌.

git add filename
git add .
 - add 명령을 통해 파일 추적할 수 있도록 해 줌. stage에 올림.

git reset HEAD --
 - git add 한 것을 되돌리고 싶을 때 사용.

git commit -m "description"
git commit -am "description"
 - description 을 바로 인라인으로 입력.
git commit -a 
 - add 하고 commit을 해야 하지만, add 부분을 포함해서 바로 커밋 하는 것. 
git commit —amend
 - 지역저장소에 버전을 수정할 때 사용.
   (원격저장소에 push한 후에는 수정하지 말 것.)

git init —bare 저장소이름
 - 수정 등을 할 수 없고, 단지 그냥 저장만 가능한 저장소의 역할.

git reset f1756b3949eab561ebcef39f1560beaaceeb6cf2 —-hard
 - 커밋 넘버를 포함하는 부분까지 리셋됨. (즉 5,4,3,2,1 버전이 있을 때 리셋 3을 하면 4,5 가 없어지는 것임.)
 - 원격 저장소에 올려서 협업을 하는 경우에, 리셋 절대 금지. 내 컴퓨터의 버전을 관리할 경우에만 사용해야 함

git remote add origin 주소(http….)
 - 내 로컬저장소에 원격저장소(주소)를 origin이라는 별명을 써서 추가하겠다. 

git checkout commit no.
 - 해당 커밋 넘버의 커밋 당시의 파일로 넘어감.
   (master —> 해당 브랜치 이름으로 넘어감)

git push -u origin master
 - 푸쉬를 하는데 -u origin master 옵션을 사용해서 
   내 로컬저장소와 origin으로 별명을 지은 원격저장소의 마스터 브랜치를 연결하겠다는 뜻. 
   이렇게 하면, 다음부터는 -u origin master 없이 그냥 git push 만 하면 됨.
git push origin <branch name>
 - <branch name> 에 푸쉬 할 때 명령어.

git log —-reverse
 - 거꾸로 깃의 로그를 볼 수 있다. 


git pull
 - 원격저장소에 있는 자료를 끌어오는 것.

git branch <branch name>
 - 브랜치만들기

git checkout <branch name>
 - 해당 브랜치로 전환하기

git checkout -b <branch name>
 - 브랜치 작성과 전환을 한꺼번헤 하기.

git config —global user.name “your nickname”
git config —global user.email “your email”

git revert 
 - 리셋을 하면서 그 부분에 다른 것을 집어 넣는 것.
 




사이트
https://git-scm.com/book/ko/v1/Git%EC%9D%98-%EA%B8%B0%EC%B4%88-Git-%EC%A0%80%EC%9E%A5%EC%86%8C-%EB%A7%8C%EB%93%A4%EA%B8%B0




정리 안 된 부분


git clone 클론할 깃주소 | 폴더만들 경우 이곳에 생성할 폴더 이름넣으면 됨
ex)
git clone address gitsrc
gitsrc 폴더를 만들어서 그곳에 깃주소에 해당하는 것을 복제함

git clone address .
. 은 현재 디렉토리를 의미함


git stash save
git stash pop

## Setup

`git clone <repository>`

## Start work

* Checkout master `git checkout master`
* Pull in latest changes from master `git pull`
* Start working on new feature/create branch: `git checkout -b my_new_feature_branch`

## Work

* Commit changes locally: `git commit -am "your commit message"` - -a: adds all changes - -m: set commit message
* Push changes to bitbucket: `git push origin my_new_feature_branch` - Creates the new branch on bitbucket

## Squashing commits

* Start interactive rebase: `git rebase -i HEAD~3`
* In case of conflicts, see below
* This opens the editor and allows you to modify the commit history
* Once you have saved your changes in your editor, the changes are applied locally
* Push to bitbucket: `git push --force-with-lease origin my_new_feature_branch`

## Merge

* Squash commits if multiple commits in branch (see below)
* Rebase on master before merging: `git pull --rebase origin master` - See below for when there is a conflict
* Go to bitbucket to create pull request, gather reviews and approval and then merge.
* git push —force-with-lease origin my_new_feature_branch

## In case of conflicts

* When doing the `git pull --rebase`, you will enter the interactive rebase mode - See conflicting changes: `git status` - All unstated files have conflicts - Open and resolve conflicts in each conflicting files - Set as resolved by staging files: `git add <file_name>` - Complete rebase: `git rebase --continue`
* Push rebased changes: `git push --force-with-lease origin my_new_feature_branch

