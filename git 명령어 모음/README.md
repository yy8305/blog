# git 명령어 모음

## 소스 업로드 관련

- 로컬 커밋(commit)
    
    ```
    $ git commit -m "설명"
    ```

- 원격 푸쉬(push)

    ```
    $ git push origin <branch name>
    ex) git push origin master
    ```

## 소스 다운로드 관련

- 원격(remote) 전체 내려받기

    ```
    $ git clone <url>
    ```

- 현재 소스에서 

## git branch 관련

- 원격(remote), 로컬 브랜치 전체 확인

    ```
    $ git branch -a

    ---출력---
    * master
    remotes/origin/HEAD -> origin/master
    remotes/origin/master
    remotes/origin/v1
    ```

- 원격(remote) 브랜치 확인

    ```
    $ git branch -r

    ---출력---
    origin/HEAD -> origin/master
    origin/master
    origin/v1
    ```

- 원격(remote) 브랜치 가져오기

    ```
    $ git checkout -t origin/<branchname>
    ```

- 브랜치 삭제

    ```
    # 로컬(local)
    $ git branch -d <branchname>


    # 원격(remote)
    $ git push origin :<branchname>
    ```

## git remote(원격) 관련

- 원격(remote) 연결
    ```
    $ git remote add <이름> <url>
    ex) git remote add origin http://~
    ```

- 현재 연결된 원격(remote)정보 확인

    ```
    $ git remote -v

    ---출력---
    origin  https://github.com/~~ (fetch)
    origin  https://github.com/~~ (push)
    ```