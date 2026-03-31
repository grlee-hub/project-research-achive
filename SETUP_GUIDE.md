# 🚀 Research Archive — GitHub Pages 설정 가이드

## 1단계: GitHub 저장소 만들기

1. [github.com](https://github.com) 접속 → 로그인
2. 우측 상단 **+** → **New repository**
3. 설정:
   - Repository name: `research-archive` (원하는 이름으로)
   - Visibility: **Public** (GitHub Pages 무료 사용 조건)
   - README 추가 체크: ✅
4. **Create repository** 클릭

---

## 2단계: GitHub Pages 활성화

1. 저장소 페이지 → **Settings** 탭
2. 좌측 메뉴 → **Pages**
3. Branch: `main` 선택 → `/ (root)` 선택 → **Save**
4. 잠시 후 `https://{username}.github.io/research-archive` 로 접속 가능

---

## 3단계: 각 기기에서 저장소 연결

### 맥북 / 맥미니

```bash
# git 설치 확인
git --version

# 저장소 클론 (최초 1회)
git clone https://github.com/{username}/research-archive.git
cd research-archive

# index.html을 이 폴더에 복사해 넣기
cp /path/to/index.html .
git add index.html
git commit -m "첫 번째 커밋: 아카이브 웹사이트 추가"
git push
```

### Climate 서버

```bash
# 서버에 SSH 접속 후
git clone https://github.com/{username}/research-archive.git
cd research-archive
```

> **인증 방법**: Personal Access Token 사용 권장
> GitHub → Settings → Developer settings → Personal access tokens → Generate new token (repo 권한 체크)

---

## 4단계: 파일 업로드하는 법

### 파일 구조 예시

```
research-archive/
├── index.html          ← 웹사이트 메인 파일
├── papers/
│   └── climate_validation.pdf
├── notes/
│   └── bias_correction_idea.md
├── code/
│   └── era5_download.py
└── data/
    └── korea_temp_trend.png
```

### 새 파일 추가 & 업로드

```bash
# 파일을 해당 폴더에 복사
cp 새논문.pdf papers/

# 업로드
git add .
git commit -m "2026-03-31 기후모델 실험 결과 추가"
git push
```

→ 약 30초~1분 후 웹사이트에 자동 반영

---

## 5단계: index.html에 새 항목 추가

`index.html` 파일을 열고 `items` 배열에 항목을 추가합니다:

```javascript
{
  type: "paper",        // paper | note | code | data
  icon: "📄",
  title: "논문 제목",
  desc: "간단한 설명",
  date: "2026-03-31",
  link: "papers/파일명.pdf",
  linkLabel: "PDF 열기",
  tags: ["태그1", "태그2"]
},
```

수정 후 `git add index.html && git commit -m "항목 추가" && git push`

---

## 자주 쓰는 명령어 요약

| 목적 | 명령어 |
|------|--------|
| 최신 상태 받기 | `git pull` |
| 파일 추가/수정 반영 | `git add . && git commit -m "메모" && git push` |
| 변경사항 확인 | `git status` |
| 업로드 내역 확인 | `git log --oneline` |

---

## 팁

- **여러 기기 동기화**: 작업 전에 항상 `git pull` 먼저 실행
- **100MB 이상 파일**: GitHub LFS 사용 (`git lfs track "*.nc"`)
- **비공개로 바꾸고 싶을 때**: Settings → General → Change visibility → Private
