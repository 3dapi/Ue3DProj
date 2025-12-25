# 초보자를 위한 언리얼 엔진 5.1 게임 프로그래밍  
(Introduction to Game Programming with Unreal Engine)

## Development Environment
- Unreal Engine 5.1
- Blueprints

## 📢 [공지] Git LFS 전환에 따른 로컬 환경 초기화 안내 (필수)

프로젝트의 에셋 관리 방식이 Git LFS (Large File Storage) 로 전환되었습니다.
기존 로컬 저장소를 유지한 상태에서 작업을 계속하려면 아래 절차를 반드시 순서대로 실행해 주세요.

## ⚠️ 중요 안내
- 아래 과정에는 git reset --hard, git clean -fxd 명령이 포함되어 있습니다.
- 커밋되지 않은 모든 로컬 파일(코드, 에셋, 테스트 파일 등)은 전부 삭제됩니다.
- 필요한 파일은 반드시 미리 백업하세요.
- 실행 전 Unreal Engine Editor, Visual Studio 를 반드시 종료하세요.


### 1. Git LFS 설치 여부 확인
- 터미널(Git Bash 또는 CMD)에서 아래 명령어를 실행합니다.

  ```bash
  where git-lfs
  ```

- 아래와 같이 git-lfs.exe 경로가 출력되면 이미 설치된 상태입니다. → 바로 2단계로 이동하세요.
 
  ```bash
  <full-path>\git-lfs.exe
  ```

- 아무 경로도 출력되지 않고 아래 메시지가 나오면 설치되지 않은 상태입니다.
- 이 경우 아래 링크에서 Git LFS를 설치한 뒤, 터미널을 완전히 종료했다가 다시 실행하고 다시 where git-lfs 명령으로 확인하세요.

- Git LFS 공식 사이트: https://git-lfs.github.com/


### 2. 저장소 강제 초기화 및 정리 (필수)
- ⚠️ 이 단계부터 로컬 작업물은 모두 삭제됩니다. 아래 명령어를 한 줄씩 순서대로 실행하세요.

  ```bash
  git lfs install

  정상 출력 예:  Git LFS initialized.

  git fetch origin
  git reset --hard origin/main

  출력 예:
  Updating files: 100% (5370/5370), done.
  HEAD is now at d490c62 Merge remote-tracking branch 'origin/main'

  git clean -fxd
  ```
  
- 이 과정에서 다음과 같은 자동 생성 폴더들이 삭제됩니다.
  - Binaries
  - Intermediate
  - Saved
- 기타 캐시 파일

  ```bash
  git lfs pull
  이 단계에서 .uasset, .umap 등 실제 바이너리 에셋 파일이 다운로드됩니다.
  ```

### 3. 완료 확인
- 아래 명령어를 실행했을 때 에셋 목록이 출력되면 정상 완료입니다.

  ```bash
  git lfs ls-files
  ```
  
  Unreal Engine 실행 시 Binaries 폴더 삭제로 인해
Rebuild 하겠냐는 메시지가 나올 수 있으며,
이는 정상 동작이므로 그대로 진행하시면 됩니다.

#### <정리>
- Git LFS 전환 후 기존 로컬 저장소를 정상화하기 위한 필수 절차입니다.
- 순서 변경 ❌ / 중간 생략 ❌
- 문제 발생 시 중간에서 멈추지 말고 로그 전체를 공유해 주세요.
