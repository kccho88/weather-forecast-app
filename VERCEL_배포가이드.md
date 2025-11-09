# 🌤️ 날씨 웹앱 Vercel 배포 가이드

## 📦 방법 1: 파일 직접 업로드 (가장 쉬움!)

### 준비물
현재 프로젝트의 다음 파일들:
- ✅ index.html
- ✅ style.css
- ✅ script.js
- ✅ vercel.json
- ✅ package.json

### 단계별 가이드

#### 1️⃣ Vercel 계정 만들기
1. https://vercel.com 접속
2. "Sign Up" 클릭
3. GitHub, GitLab, 또는 이메일로 가입
4. 이메일 인증 완료

#### 2️⃣ 프로젝트 폴더 압축하기
1. `weatherapi` 폴더 전체를 선택
2. 마우스 우클릭 → "압축" 또는 "Send to" → "Compressed folder"
3. `weatherapi.zip` 파일 생성됨

#### 3️⃣ Vercel에 업로드
1. Vercel 대시보드에서 "Add New..." → "Project" 클릭
2. 아래로 스크롤하여 "Deploy from a template" 섹션 찾기
3. 또는 직접 https://vercel.com/new 접속

**주의**: Vercel은 직접 ZIP 업로드를 지원하지 않습니다!
GitHub 연동이 필요합니다.

---

## 📦 방법 2: GitHub 연동 배포 (권장)

### 1️⃣ GitHub 저장소 만들기

#### A. GitHub 웹사이트에서
1. https://github.com 로그인
2. 우측 상단 "+" → "New repository" 클릭
3. Repository name: `weather-forecast-app` 입력
4. Public 선택
5. "Create repository" 클릭

#### B. 저장소 주소 복사
생성된 저장소의 URL 복사 (예: https://github.com/your-username/weather-forecast-app.git)

### 2️⃣ 로컬 Git 설정

터미널에서 다음 명령어 실행:

```bash
# weatherapi 폴더로 이동
cd c:\Users\PC\Desktop\Cursor_ai_exe\weatherapi

# Git 초기화 (이미 되어있다면 스킵)
git init

# 파일 추가
git add .

# 커밋
git commit -m "Initial commit: Weather forecast app"

# GitHub 저장소 연결 (your-username을 본인 GitHub 아이디로 변경!)
git remote add origin https://github.com/your-username/weather-forecast-app.git

# 푸시
git branch -M main
git push -u origin main
```

### 3️⃣ Vercel에서 GitHub 저장소 연동

1. https://vercel.com 로그인
2. "Add New..." → "Project" 클릭
3. "Import Git Repository" 선택
4. GitHub 연결 허용
5. 방금 만든 저장소 선택
6. "Import" 클릭
7. 프로젝트 설정:
   - **Project Name**: weather-forecast-app (원하는 이름)
   - **Framework Preset**: Other (또는 자동 감지)
   - **Root Directory**: ./
   - 나머지는 기본값 사용
8. "Deploy" 클릭!

### 4️⃣ 배포 완료! 🎉

- 배포 진행 상황을 실시간으로 확인할 수 있습니다
- 완료되면 URL이 생성됩니다: `https://weather-forecast-app.vercel.app`
- 이 URL을 클릭하면 웹앱을 볼 수 있습니다!

---

## 📦 방법 3: Vercel CLI 사용 (고급)

### 1️⃣ 설치 및 로그인
```bash
# Vercel CLI 설치 (이미 완료)
npm install -g vercel

# 로그인
vercel login
```

### 2️⃣ 브라우저에서 인증
1. 터미널에 표시된 URL 복사 (예: https://vercel.com/oauth/device?user_code=XXXX-XXXX)
2. 브라우저에서 해당 URL 열기
3. Vercel 계정으로 로그인
4. "Confirm" 또는 "Authorize" 클릭
5. 터미널로 돌아와서 Enter 키 누르기

### 3️⃣ 배포
```bash
# weatherapi 폴더에서
cd c:\Users\PC\Desktop\Cursor_ai_exe\weatherapi

# 배포 시작
vercel

# 질문에 답변:
# - Set up and deploy? Y
# - Which scope? (본인 계정 선택)
# - Link to existing project? N
# - What's your project's name? weather-forecast-app
# - In which directory is your code located? ./
# - Want to override the settings? N

# 프로덕션 배포
vercel --prod
```

---

## 🔧 문제 해결

### Git 충돌 문제
기존 저장소와 충돌이 있다면:

```bash
# 새로운 저장소로 시작
cd c:\Users\PC\Desktop\Cursor_ai_exe\weatherapi
rm -rf .git  # 기존 git 삭제 (Windows에서는 폴더 직접 삭제)
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/your-username/new-repo.git
git push -u origin main
```

### Vercel 로그인 안 됨
1. 브라우저 쿠키/캐시 삭제
2. 시크릿 모드에서 로그인 시도
3. 다른 브라우저 사용

### 배포 후 사이트가 안 보임
1. Vercel 대시보드에서 배포 로그 확인
2. 파일 경로가 올바른지 확인
3. vercel.json 설정 확인

---

## ✅ 배포 확인 체크리스트

- [ ] Vercel 계정 생성 완료
- [ ] GitHub 저장소 생성 (방법 2 사용 시)
- [ ] 코드 푸시 완료 (방법 2 사용 시)
- [ ] Vercel에서 프로젝트 Import
- [ ] 배포 성공
- [ ] 생성된 URL에서 웹앱 확인
- [ ] 날씨 검색 기능 테스트

---

## 🎯 추천 방법

**초보자**: 방법 2 (GitHub 연동) 추천!
- 가장 안정적
- 자동 배포 지원
- 코드 변경 시 자동으로 재배포

**빠른 테스트**: 방법 3 (CLI) 
- 명령어 한 번으로 배포
- GitHub 없이 가능

---

## 📞 도움이 필요하면

1. Vercel 공식 문서: https://vercel.com/docs
2. Vercel Discord: https://vercel.com/discord
3. GitHub 가이드: https://docs.github.com/ko

배포 성공을 기원합니다! 🚀

