# 개인 연구 홈페이지

이 저장소는 **HTML과 CSS만 사용한 개인 연구 홈페이지**입니다. 별도의 설치나 빌드 과정 없이 GitHub Pages에서 바로 공개할 수 있습니다.

## 왜 Jekyll 대신 HTML/CSS인가요?

- HTML은 사이트의 **내용과 구조**, CSS는 **디자인**을 담당합니다.
- GitHub Pages가 파일을 그대로 공개하므로 설치·업데이트·보안 관리가 거의 없습니다.
- 논문이나 소식이 많아져 반복 편집이 불편해질 때 Jekyll로 옮겨도 늦지 않습니다.
- `.nojekyll` 파일은 GitHub Pages가 이 사이트를 Jekyll 프로젝트로 처리하지 않도록 알려 줍니다.

## 파일 구조

```text
.
├── index.html          # 홈과 모든 연구 섹션
├── cv.html             # 인쇄/PDF 저장이 가능한 CV 페이지
├── styles.css          # 색상, 글꼴, 간격, 모바일 화면 디자인
├── assets/
│   └── favicon.svg     # 브라우저 탭 아이콘
├── .nojekyll           # 정적 사이트라는 표시
└── README.md           # 지금 읽고 있는 안내서
```

## 1단계: 내 정보로 바꾸기

코드 편집기에서 프로젝트 전체 검색을 사용해 아래 항목을 교체하세요.

| 현재 문구 | 바꿀 내용 |
| --- | --- |
| `Your Name` | 영문 이름 |
| `YN` | 영문 이니셜 |
| `Your Current Position` | 현재 직책 |
| `Your Department` | 소속 학과/부서 |
| `Your University or Institute` | 대학 또는 연구기관 |
| `your.email@university.edu` | 이메일 |
| `City, Country` | 활동 지역 |

그다음 `index.html`의 연구 설명, 논문, 프로젝트, 소식, 프로필 링크를 실제 정보로 수정하세요. HTML 주석은 화면에 보이지 않으므로 나중에 편집 메모를 남길 때 `<!-- 메모 -->` 형식을 사용할 수 있습니다.

프로필 사진을 넣으려면:

1. 사진을 `assets/profile.jpg`로 저장합니다.
2. `index.html`에서 `portrait-placeholder`가 있는 `<div>...</div>` 전체를 아래 한 줄로 바꿉니다.

```html
<img class="portrait-placeholder" src="assets/profile.jpg" alt="Portrait of Your Name" />
```

## 2단계: 내 컴퓨터에서 확인하기

가장 간단한 방법은 `index.html` 파일을 더블클릭해 브라우저에서 여는 것입니다. 링크와 글꼴까지 웹사이트와 똑같이 확인하려면 이 폴더에서 작은 로컬 서버를 실행합니다.

```bash
python3 -m http.server 8000
```

브라우저에서 `http://localhost:8000`을 열고, 작업이 끝나면 터미널에서 `Control + C`를 누릅니다.

## 3단계: Git으로 첫 버전 기록하기

Git은 파일의 변경 이력을 저장합니다. 아래 명령은 이 폴더를 Git 저장소로 만들고 첫 버전을 기록합니다.

```bash
git init
git add .
git commit -m "Create initial academic website"
git branch -M main
```

- `git init`: 현재 폴더에서 버전 관리를 시작합니다.
- `git add .`: 현재 파일을 다음 기록에 포함합니다.
- `git commit`: 포함한 파일을 하나의 버전으로 저장합니다.
- `git branch -M main`: 기본 브랜치 이름을 `main`으로 정합니다.

## 4단계: GitHub 저장소 만들기

1. GitHub에 로그인하고 오른쪽 위 `+` → **New repository**를 선택합니다.
2. 저장소 이름은 `사용자이름.github.io`를 권장합니다. 예: GitHub 사용자 이름이 `janedoe`라면 `janedoe.github.io`입니다.
3. **Public**을 선택합니다.
4. README, `.gitignore`, license 추가 옵션은 선택하지 않습니다. 이미 로컬에 README가 있기 때문입니다.
5. **Create repository**를 누릅니다.

이름을 정확히 `사용자이름.github.io`로 만들면 주소가 `https://사용자이름.github.io`가 됩니다. 다른 저장소 이름을 쓰면 `https://사용자이름.github.io/저장소이름/`에서 공개됩니다.

## 5단계: 로컬 파일을 GitHub에 올리기

GitHub가 새 저장소 화면에 보여 주는 주소를 복사하고 아래 `YOUR-USERNAME`을 바꿉니다.

```bash
git remote add origin https://github.com/YOUR-USERNAME/YOUR-USERNAME.github.io.git
git push -u origin main
```

- `remote`는 내 컴퓨터의 저장소와 GitHub 저장소를 연결합니다.
- `push`는 로컬 커밋을 GitHub로 보냅니다.

## 6단계: GitHub Pages 켜기

1. GitHub 저장소에서 **Settings** → **Pages**로 이동합니다.
2. **Build and deployment**의 Source를 **Deploy from a branch**로 선택합니다.
3. Branch는 `main`, 폴더는 `/(root)`를 선택하고 **Save**를 누릅니다.
4. 몇 분 뒤 같은 화면에 공개 주소가 표시됩니다.

`사용자이름.github.io` 저장소는 Pages가 자동으로 켜지는 경우도 있지만, 위 화면에서 공개 주소가 생겼는지 확인하는 것이 가장 확실합니다.

## 7단계: 이후 내용 업데이트하기

파일을 수정하고 브라우저에서 확인한 뒤 아래 세 명령을 반복합니다.

```bash
git status
git add .
git commit -m "Update publications and news"
git push
```

좋은 커밋 메시지는 “무엇을 바꿨는지” 짧게 설명합니다. 예: `Add new publication`, `Update CV`, `Replace profile photo`.

## 공개 전 점검표

- [ ] 이름, 소속, 이메일, 지역을 실제 정보로 교체했다.
- [ ] 가짜 논문 예시를 모두 실제 논문으로 교체했다.
- [ ] Google Scholar, ORCID, GitHub, LinkedIn 링크를 넣었다.
- [ ] 프로필 사진과 대체 텍스트를 넣었다.
- [ ] CV의 학력, 경력, 수상, 기술을 수정했다.
- [ ] 휴대폰 화면에서도 확인했다.
- [ ] 공개하고 싶지 않은 전화번호, 집 주소, 개인 정보가 없는지 확인했다.

## 다음 확장 아이디어

논문과 소식이 수십 개로 늘어나면 Jekyll의 데이터 파일이나 컬렉션을 도입할 수 있습니다. 그 전까지는 지금 구조가 가장 배우기 쉽고 관리 부담이 적습니다.
