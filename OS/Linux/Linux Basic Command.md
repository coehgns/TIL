# Linux Basic Command

#### ls
- `ls` : 현재 디렉토리의 파일 및 폴더들을 로드합니다.
![image](https://github.com/user-attachments/assets/e7e998c2-501c-4ed4-8871-a2d2dfc36ddc)

- `ls -l` : 현재 디렉토리의 파일 및 폴더들의 자세한 정보들을 함께 로드합니다.
![image](https://github.com/user-attachments/assets/e18fb35a-4de9-4cf0-8180-e43994749ce0)

- `ls -a` : 현재 디렉토리의 숨겨진 파일들을 포함하여 함께 로드합니다.
![image](https://github.com/user-attachments/assets/d86064d8-a938-43ec-8861-8a2f93832393)

#### cd
- `cd` : 디렉토리를 변경합니다.
- `cd 폴더이름` : 해당 폴더로 디렉토리를 이동합니다.
![image](https://github.com/user-attachments/assets/cff0c550-14c1-4bda-be9b-593126e8b653)

- `cd ..` : 현재 디렉토리의 상위 폴더를 이동합니다.
![image](https://github.com/user-attachments/assets/e6969767-b742-4998-8d6a-ff95a5759fc0)

#### pwd
- `pwd` : 현재 디렉토리의 폴더 경로를 표시해줍니다.
![image](https://github.com/user-attachments/assets/f6e917c6-2b28-4e18-9ea7-83a9aaed37f3)

#### mkdir
- `mkdir` : 새로운 디렉토리를 생성합니다.
- `mkdir 디렉토리이름` : 디렉토리이름에 해당하는 디렉토리를 생성합니다.
- `mkdir -p 폴더이름1/폴더이름2` : 폴더이름1 폴더 안에 폴더이름2 폴더를 생성합니다.
![image](https://github.com/user-attachments/assets/8ba5aa31-6bb1-42fc-9f49-10ad07a4841f)

#### rmdir
- `rmdir 폴더이름` : 폴더이름에 해당하는디렉토리를 삭제합니다.
![image](https://github.com/user-attachments/assets/3d509338-ef23-4af0-9e6e-7a7b3ef9ecca)

#### rm
- `rm file` : file을 삭제합니다.
- `rm folder` : folder를 삭제합니다.
![image](https://github.com/user-attachments/assets/256abc9c-1596-4961-bdd8-f727ed3d8290)

- `rm -r 폴더이름` : 해당 폴더 디렉토리와 그 안에 있는 모든 내용을 삭제합니다.
![image](https://github.com/user-attachments/assets/3b9e1ea8-190c-4d6f-906e-d223df3aaeb3)

#### touch
- `touch` : 새로운 빈 파일을 생성하거나, 현재 시간을 기준으로 타임스탬프를 갱신합니다.
![image](https://github.com/user-attachments/assets/5e131923-204a-4af4-8c37-f5b144c1a705)

#### cp
- `cp folder1 folder2` : folder1을 folder2에 복사합니다.
- `cp -r folder1 folder2` : foldre1과 그 안에 있는 내용을 folder2에 복사합니다.

#### mv
- `mv` : 파일이나 디렉토리를 이동시키거나 이름을 변경합니다.
- `mv Language language` : Language 디렉토리를 language로 이름을 변경합니다.
- `mv file.txt /dekstop/TIL/OS` : file.txt 파일을 해당 경로로 이동합니다.

#### cat
- `cat` : 해당 파일의 내용을 출력하거나 여러 파일을 연결하여 출력할 수 있습니다.
- `cat devops란.md` : 해당 파일의 내용을 출력합니다.
![image](https://github.com/user-attachments/assets/9edb2d0f-a3c4-4bdf-be15-2b09aceb0b72)

- `cat file1.txt file2.txt > file3.txt` : file1의 내용과 file2의 내용을 합쳐 file3.txt에 저장합니다.

#### chmod
- `chmod` : 파일이나 디렉토리의 권한을 변경합니다.

#### grep
- `grep "token" 'Access Token과 Refresh Token.md'` : `Access Token과 Refresh Token.md`이라는 파일 안에서 "token"라는 문자열이 포함된 모든 줄을 출력합니다.
![image](https://github.com/user-attachments/assets/a3956080-6a4d-422a-b8c6-1be5232bbf69)
- `grep -r "token" .` : 현재 디렉토리와 하위 디렉토리에서 "token"이라는 문자열을 재귀적으로 출력합니다.
![image](https://github.com/user-attachments/assets/7e55aad4-e952-4b3a-aebf-7b90ae235f04)

#### echo
- `echo Hello World` : 해당 문자열을 출력합니다. 
`echo`를 사용해 환경 변수를 출력할 수도 있습니다.
![image](https://github.com/user-attachments/assets/384ae7b9-8850-4e2d-8c14-a600c5c61301)
- `echo "Hello World" > file.txt` : `Hello World`라는 문자열을 file.txt 파일에 저장합니다.

#### sudo(SupperUser Do)
- 일반 사용자가 관리자 권한을 가지고 명령어를 사용할 수 있습니다.
- `sudo ...`

#### find
- 파일이나 디렉토리를 찾습니다.
- `find . -name 'file.txt'` : 현재 디렉토리에서 file.txt라는 파일을 찾습니다.

## 참고 자료
- https://velog.io/@tngus0325/16%EA%B0%80%EC%A7%80-%EB%A6%AC%EB%88%85%EC%8A%A4-%EA%B8%B0%EB%B3%B8-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%A0%95%EB%A6%AC