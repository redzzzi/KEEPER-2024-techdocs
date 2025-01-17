아래는 가장 많이 사용되는 git 명령어 모음 링크입니다.
https://docs.gitlab.com/ee/topics/git/commands.html

# 리액트 앱 생성
- CI/CD 파이프라인 테스트를 위해 간단히 리액트 앱을 생성 후 테스트하였습니다. 간단한 설명과 명령어들을 작성하였습니다.
- 생성 명령어
  - 기본적으로 아래의 명령어로 리액트 앱을 생성할 수 있습니다. 타입스크립트를 사용하고 싶다면 명령어 말미에 `--template typescript`를 추가할 수 있습니다.
  - npx는 npm에서 제공하는 도구로, Node.js 설치 시 제공이 됩니다.
```wsl
npx create-react-app <앱 이름>
```
- 패키지 관리자
  - 리액트는 개발 및 빌드 시 Node.js를 기반으로 실행됩니다. 원하는 버전을 선택하여 운용해볼 수 있습니다.
  - 패키지 관리자는 `npm` 또는 `yarn`가 있습니다. 보통 `npm`을 많이 사용하며, `yarn`을 사용하고 싶다면 `npm install yarn` 명령어를 사용할 수 있습니다.
  - `yarn`이 `npm`과 비교했을 때 안정적이고 종속성 관리 측면에서 우위에 있다고 합니다. <sub>하지만 제가 각각을 사용해보았을 때 일반 학부생 프로젝트 수준에서는 차이를 느끼지 못했습니다...</sub>
- 패키지 설치 및 실행 명령어 (`npm` 기준)
  - 리액트 앱을 구성하는 노드 모듈 폴더는 무겁기 때문에 오픈소스 코드에서는 확인할 수 없습니다. 대신 `package.json` 파일을 두고 어떤 패키지를 썼는지 확인할 수 있습니다. 해당 패키지를 로컬에서 구성할 수 있도록 설치하는 명령어가 아래와 같습니다.
  - 리액트 앱을 처음에 실행하고자 한다면, `localhost:3000`로 접속됩니다.
```
npm install
```
```
npm start
```

# 도커
- Linux 기준으로 작성되었습니다.
- 도커 실행 여부 확인
```
docker info
```
- [도커 데몬](https://www.geeksforgeeks.org/what-is-docker-daemon/) 시작
```
sudo systemctl start docker
```
- 실행 중인 컨테이너 확인
```
docker ps
```
- 도커 컨테이너 시작
```
docker start <컨테이너 ID 또는 이름>
```
- **Dockerfile 사용 시 컨테이너 재빌드 및 실행**
  - 경로: 리액트 앱의 루트 경로
  - `3000:80`은 호스트의 3000번 포트에 요청이 들어오면, 이를 컨테이너 내부 80번 포트로 전달한다는 의미입니다.
```
docker build -t <앱 이름> .
```
```
docker run -p 3000:80 <앱 이름>
```

# 깃랩
- gitlab-runner 사용 (Window Powershell)
  - `gitlab-runner.exe` 설치
  - 시스템 PATH 환경 변수 추가
```powershell
& "C:\Program Files\gitlab-runner.exe" register
```
- gitlab-runner 실행 로그
```
& "C:\Program Files\gitlab-runner.exe" --debug run
```

# 기타 
## yamllint
- yml 파일의 유효성에 대해 판단해주는 도구입니다.
- 설치
```
sudo apt-get install yamllint
```
- 이용
```
yamllint <파일명>
```
![image](https://github.com/user-attachments/assets/ff471317-9df9-4e6f-aaff-967205e8a1d4)
