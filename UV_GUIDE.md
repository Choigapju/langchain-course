# UV 패키지 매니저 사용 가이드

## 🎯 가상환경 관리

### ✅ 권장: uv run 사용

가상환경을 직접 활성화하지 않고 `uv run`을 사용하세요:

```bash
# Python 스크립트 실행
uv run python main.py

# 패키지 도구 실행
uv run black .
uv run isort .

# Python 인터프리터
uv run python
```

**장점:**
- 항상 올바른 가상환경 사용 보장
- 의존성 자동 동기화
- 가상환경 활성화/비활성화 불필요
- 프로젝트 디렉토리 어디서든 작동

### 📦 전통적 방식 (선택)

일반 가상환경처럼 사용도 가능합니다:

```bash
# 활성화
source .venv/bin/activate

# 사용
python main.py

# 비활성화
deactivate
```

## 📚 자주 사용하는 uv 명령어

### 의존성 관리
```bash
# 패키지 추가
uv add langchain-anthropic

# 개발 의존성 추가
uv add --dev pytest

# 패키지 제거
uv remove 패키지이름

# 의존성 동기화 (설치/업데이트)
uv sync

# pyproject.toml 변경 후 동기화
uv sync
```

### 프로젝트 실행
```bash
# 메인 스크립트 실행
uv run python main.py

# 특정 파일 실행
uv run python src/agent.py

# 모듈로 실행
uv run python -m mymodule

# 인터프리터 시작
uv run python
```

### 개발 도구 실행
```bash
# 코드 포맷팅
uv run black .
uv run isort .

# 타입 체크 (mypy 설치 시)
uv run mypy .

# 테스트 (pytest 설치 시)
uv run pytest
```

### 가상환경 관리
```bash
# 가상환경 생성 (자동)
uv sync

# 가상환경 삭제
rm -rf .venv

# 가상환경 재생성
rm -rf .venv && uv sync

# Python 버전 변경
echo "3.10" > .python-version
uv sync
```

## 💡 유용한 팁

### 1. 별칭(Alias) 설정
자주 사용하는 명령어를 짧게 만들기:

```bash
# ~/.zshrc 또는 ~/.bashrc에 추가
alias uvr="uv run python"
alias uvt="uv run pytest"
alias uvf="uv run black . && uv run isort ."

# 사용 예시
uvr main.py
```

### 2. 프로젝트별 Python 버전
```bash
# .python-version 파일로 Python 버전 고정
echo "3.10" > .python-version
uv sync
```

### 3. 빠른 패키지 테스트
```bash
# 일회성으로 패키지 테스트 (설치 없이)
uvx ruff check .
uvx black --check .
```

### 4. 의존성 업데이트
```bash
# 모든 패키지 최신 버전으로 업데이트
uv sync --upgrade

# 특정 패키지만 업데이트
uv add langchain@latest
```

## 🆚 uv vs 다른 도구 비교

| 작업 | uv | pip + venv | poetry |
|------|----|-----------| -------|
| 가상환경 생성 | `uv sync` | `python -m venv .venv` | `poetry install` |
| 패키지 설치 | `uv add pkg` | `pip install pkg` | `poetry add pkg` |
| 스크립트 실행 | `uv run python main.py` | `source .venv/bin/activate && python main.py` | `poetry run python main.py` |
| 속도 | ⚡ 매우 빠름 | 보통 | 보통 |

## 🎯 실전 워크플로우

### 일반적인 개발 흐름
```bash
# 1. 프로젝트 디렉토리로 이동
cd /Users/choigapju/Desktop/Udemy/LangChain

# 2. 새 패키지 추가가 필요하면
uv add 새패키지

# 3. 코드 작성
code main.py

# 4. 실행 및 테스트
uv run python main.py

# 5. 포맷팅
uv run black .
uv run isort .

# 6. Git 커밋
git add .
git commit -m "feat: 새 기능 추가"
git push
```

### 새 브랜치로 전환할 때
```bash
# 1. 브랜치 전환
git checkout project/ReAct-search-agent

# 2. 의존성 동기화 (중요!)
uv sync

# 3. 실행
uv run python main.py
```

## 🚫 주의사항

1. **conda와 함께 사용하지 마세요**
   - conda 환경이 활성화되어 있으면 비활성화
   - `conda deactivate`

2. **브랜치 전환 후 uv sync 필수**
   - 각 브랜치마다 의존성이 다를 수 있음
   - `git checkout` 후 항상 `uv sync` 실행

3. **pyproject.toml 수동 편집 후**
   - 반드시 `uv sync` 실행
   - 의존성을 실제로 설치/업데이트

## 🔗 추가 리소스

- [uv 공식 문서](https://docs.astral.sh/uv/)
- [uv GitHub](https://github.com/astral-sh/uv)

