## vscode 패키지 에러
- 에러내용
```
N: Skipping acquire of configured file 'main/binary-arm64/Packages' as repository 'http://packages.microsoft.com/repos/vscode stable InRelease' doesn't support architecture 'arm64'
N: Skipping acquire of configured file 'main/binary-armhf/Packages' as repository 'http://packages.microsoft.com/repos/vscode stable InRelease' doesn't support architecture 'armhf'
```

- 해결방법
```
에러 내용을 보아하니 apt vscode 패키지에서 에러가 난듯하다.

1. 해당 파일을 열어본다.
$ sudo vi /etc/apt/sources.list.d/vscode.list

2. 아래 내용대로 deb 뒤에 자신의 버전에 맞게 적어준다.(저의경우 amd64이므로 저렇게 적어줬습니다.)
deb [arch=amd64] http://packages.microsoft.com/repos/vscode stable main

3. 업데이트
$ sudo apt-get update
```
