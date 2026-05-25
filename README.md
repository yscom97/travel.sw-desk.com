# travel.sw-desk.com

가족 여행 일정과 가이드를 모아 공개하는 정적 사이트. GitHub Pages로 호스팅하고 `travel.sw-desk.com` 서브도메인으로 서비스한다.

## 구조

```
.
├── CNAME                    # "travel.sw-desk.com" (변경 금지)
├── index.html               # 랜딩(여행 목록 카드)
├── shanghai-2026-06/
│   └── index.html           # 상하이 3대 대가족 일정 (2026-06-17~21)
└── assets/                  # 향후 공통 CSS/이미지
```

각 여행은 `<destination>-<YYYY>-<MM>/index.html` 형식 폴더 하나로 관리한다.

## 업데이트 워크플로

### 기존 일정 수정
1. 해당 폴더의 `index.html`을 편집
2. `git add` → `git commit -m "..."` → `git push`
3. 1~2분 후 사이트에 반영됨

### 새 여행 추가
1. `<destination>-<YYYY>-<MM>/index.html` 폴더와 파일을 새로 만든다
2. 루트 `index.html`의 `여행 일정` 섹션에 카드 한 장을 추가한다 (기존 상하이 카드 복사·수정)
3. commit & push

## 배포

- GitHub Pages, `main` 브랜치 루트
- 푸시 후 1~2분 내 자동 빌드 / 배포
- HTTPS는 GitHub Pages가 Let's Encrypt 자동 발급 (Settings → Pages → "Enforce HTTPS" 체크)

## DNS

도메인 등록업체에서 다음 CNAME 레코드가 설정되어 있어야 한다:

```
travel.sw-desk.com  CNAME  yscom97.github.io
```

## 의존성

- Tailwind CSS (CDN, `https://cdn.tailwindcss.com`)
- Font Awesome 6.4 (CDN)
- 상하이 일정 페이지는 Chart.js 사용

별도 빌드 단계 없음. 정적 HTML.
