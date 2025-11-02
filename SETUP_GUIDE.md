# LangChain 프로젝트 개발 환경 가이드

## 🎯 현재 환경 상태

✅ **설치 완료**
- GitHub 저장소 클론 완료
- Python 3.13.3 설치됨
- uv 패키지 매니저 0.9.7 설치됨
- 프로젝트 의존성 설치 완료
- 가상환경 (.venv) 생성됨

✅ **Git 설정**
- 사용자: Choigapju
- 이메일: chgju35@gmail.com
- 원격 저장소: https://github.com/Choigapju/langchain-course.git
- 현재 브랜치: project/hello-world

## 🚀 개발 시작하기

### 1. 가상환경 활성화
```bash
cd /Users/choigapju/Desktop/Udemy/LangChain
source .venv/bin/activate
```

### 2. 환경 변수 설정
`.env` 파일을 열어 실제 API 키를 입력하세요:
```bash
# .env 파일 편집
code .env  # 또는 원하는 에디터 사용
```

필요한 API 키:
- **OPENAI_API_KEY**: https://platform.openai.com/api-keys 에서 발급
- **ANTHROPIC_API_KEY** (선택): https://console.anthropic.com/ 에서 발급
- **TAVILY_API_KEY** (선택): https://tavily.com/ 에서 발급

### 3. 프로젝트 실행
```bash
# uv를 사용한 실행
uv run python main.py

# 또는 가상환경 활성화 후 실행
source .venv/bin/activate
python main.py
```

## 📚 프로젝트 브랜치

이 코스는 여러 프로젝트로 구성되어 있으며, 각 프로젝트는 별도의 브랜치에 있습니다:

### 사용 가능한 브랜치
```bash
# 현재 브랜치 확인
git branch

# 사용 가능한 모든 브랜치 보기
git branch -a
```

### 프로젝트별 브랜치 전환
```bash
# Hello World (현재)
git checkout project/hello-world
uv sync
uv run python main.py

# ReAct Search Agent
git checkout ReAct-search-agent
uv sync
uv run python main.py
```

## 🔧 개발 워크플로우

### 코드 수정 후 커밋
```bash
# 변경사항 확인
git status

# 파일 스테이징
git add .

# 커밋
git commit -m "설명: 변경 내용"

# 원격 저장소에 푸시
git push origin project/hello-world
```

### 새로운 기능 개발
```bash
# 새 브랜치 생성
git checkout -b feature/새기능이름

# 개발 후 푸시
git push origin feature/새기능이름
```

## 🛠️ 유용한 명령어

### 의존성 관리
```bash
# 의존성 추가
uv add 패키지이름

# 의존성 제거
uv remove 패키지이름

# 의존성 업데이트
uv sync
```

### 코드 포맷팅
```bash
# Black으로 포맷팅
uv run black .

# isort로 import 정리
uv run isort .
```

## 📖 학습 경로

1. **project/hello-world** (현재) - 기본 구조와 LLM 통합
2. **ReAct-search-agent** - 검색 기능을 가진 ReAct 에이전트
3. **project/ReAct-Algo** - ReAct 알고리즘 이해
4. **project/rag-gist** - RAG 기초
5. **project/code-interpreter** - 코드 실행 및 분석

각 프로젝트는 독립적으로 실행 가능하며, 순서대로 진행하는 것을 권장합니다.

## 🔗 추가 리소스

- [LangChain 공식 문서](https://python.langchain.com/)
- [LangGraph 튜토리얼](https://langchain-ai.github.io/langgraph/tutorials/introduction/)
- [원본 코스 저장소](https://github.com/emarco177/langchain-course)

## ⚠️ 주의사항

- `.env` 파일은 **절대 커밋하지 마세요** (이미 .gitignore에 추가됨)
- API 키는 안전하게 보관하세요
- 프로젝트 브랜치 전환 시 반드시 `uv sync`를 실행하세요

