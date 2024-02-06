## Python 파이참(Pycharm) 및 아나콘다(Anaconda) 다운로드, 설치, 가상환경 연동하기 (window)


### 1. Anaconda 설치 방법

1. 아나콘다 최신 버전을 다운로드합니다.
2. 
[Anaconda 다운로드](https://www.anaconda.com/download-success)
![설치1](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/2.JPG)

![설치1](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/3-1.JPG)
![설치1](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/3-2.JPG)
![설치1](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/3-3.JPG)
![설치1](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/3-4.JPG)
![설치1](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/3-5.JPG)

 - JustMe 선택 (전체 사용은 권한 선택 불편함이 있음)
 - 기존 python이 있다면 체크 주의해서 선택(충돌 일어날 수 있음.)
   
#### 아나콘다 기본 명령어

- 아나콘다 버전 확인
  - conda -V
  - conda --version

- 가상환경 명령어
  - 아나콘다를 최신 버전으로 업데이트
    * conda update conda
  - 파이썬을 최신 버전으로 업데이트
    * conda update python
  - pip을 최신 버전으로 업데이트
    * python -m pip install --upgrade pip
  - 가상환경 생성 
    * conda create --name <가상환경이름> python=3.x

  - 현재 활성화된 가상환경의 패키지 삭제
    * conda remove <패키지이름>
  - 특정 가상환경의 패키지 삭제
    * conda remove --name <가상환경이름> <패키지이름>
  - 가상환경 삭제
    * conda env remove --name <가상환경이름>
  - 현재 활성화된 가상환경에 패키지 설지
    * conda install <패키지이름>
  - 특정 가상환경에 패키지 설치
    * conda install --name <가상환경이름> <패키지이름>
  - 특정 가상 환경에 패키지를 특정 버전으로 패키지 설치
    * conda install --name  <가상환경이름> <패키지이름>==버전

  - 가상환경 활성화
    * activate <가상환경이름>
  - 가상환경 비활성화
    * conda deactivate
   
  - 라이브러리 설치 & 삭제
    * pip install 패키지이름
    * pip install 패키지이름 --upgrade
    * pip uninstall 패키지이름
    * pip install 패키지이름==패키지버전

#### 2. Pycharm 설치 방법

### 1. 파이참 최신 버전을 다운로드합니다. 

[Pycharm 다운로드](https://www.jetbrains.com/ko-kr/pycharm/download/?section=windows)
![설치2](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/1.JPG)
- 프로페셔널 버전과 커뮤니티 버전 중 '커뮤니티 버전'을 설치합니다.
- 설치 파일을 실행하고, 설치를 시작합니다.

![설치2](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/4-1.JPG)
![설치2](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/4-2.JPG)
![설치2](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/4-3.JPG)
![설치2](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/4-4.JPG)


#### 아나콘다 가상환경 생성

- 기본설치는 [y] 선택
![설치3](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/6-1.JPG)
![설치3](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/6-2.JPG)
![설치3](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/6-3.JPG)


#### 아나콘다와 Pycharm 연동

1. Pycharm을 실행하고, 새 프로젝트를 생성합니다.
2. 가상환경을 설정하고, 프로젝트를 생성합니다.
![설치4](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/5-1.JPG)
![설치4](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/5-2.JPG)
![설치4](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/5-3.JPG)
![설치4](https://github.com/leeapgil/PythonNotes/blob/main/img/machine/5-4.JPG)

-만약 가상환경을 자동으로 찾지 못한다면 
- cmd 에서 conda init 실행
- anaconda/envs/가상환경명/Scripts/conda.exe 경로 직접 설정

