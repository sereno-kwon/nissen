# NISSEN Korea

nissen.rubiworkshop.com 원페이지 정적 사이트 (GitHub Pages). quoc.rubiworkshop.com(`sereno-kwon/quoc`)과 같은 구조와 디자인 체계입니다.

- `index.html` 한국어 원페이지 (NISSEN · RANGE · SP31 · STAINLESS OUTER · HERITAGE · CABLE GUIDE · STORY · SHOWROOM)
- 디자인은 rubi.kr과 같은 체계: 영문 Pretendard · 한글 에스코어 드림, 웨이트 400, 흑백과 얇은 라인, 각진 버튼, 라이트/다크 자동. 일본어 페이지는 빌드 시 Noto Sans JP로 바뀝니다.
- `en/index.html`, `ja/index.html` 영어 · 일본어 페이지 (빌드로 생성, 직접 수정하지 않음)
- `index.src.html` 편집용 한국어 원본. 케이블 가이드 표는 `{{CABLE_TABLE}}` 자리에 빌드 시 채워집니다 (`tools/build.py` 안의 `CABLES`).
- `i18n/` 번역 사전 (`ko.json` 원문 목록, `en.json` · `ja.json` 원문→번역)
- `tools/build.py` 한국어 페이지, 번역 페이지, sitemap.xml을 한 번에 생성
- `404.html` 하위 주소(/sp31, /outer, /heritage, /cable-guide, /dealers 등)를 섹션으로 연결
- `images/` 섹션별 이미지 (`hero`, `brand`, `sp31`, `outer`, `heritage`)
- 이미지가 아직 없는 자리는 깨진 아이콘 대신 회색 NISSEN 플레이스홀더로 보입니다.

## 처음 올릴 때
1. 이 저장소(`sereno-kwon/nissen`) main 브랜치에 푸시되어 있습니다.
2. Settings → Pages → Source: Deploy from a branch, Branch: main / (root).
3. 도메인 DNS에 `nissen` CNAME 레코드를 `sereno-kwon.github.io`로 추가하고, Pages 설정에서 Custom domain에 `nissen.rubiworkshop.com`을 넣습니다 (CNAME 파일은 이미 들어 있음). 인증서가 발급되면 Enforce HTTPS를 켭니다.
4. 이미지를 넣습니다 (아래 "이미지").
5. 파비콘과 로고: `images/favicon-48.png`, `images/favicon-96.png`, `images/apple-touch-icon.png`(180px), `images/logo-512.png`. 헤더 로고는 지금 텍스트 워드마크(`NISSEN`)입니다. 로고 이미지로 바꾸려면 quoc처럼 `<a class="logo"><img src="images/logo-white.png" ...></a>`로 교체하면 CSS가 헤더는 검정, 다크모드는 흰색으로 칠합니다.

## 이미지
1. Actions → **List Nissen product images** → Run workflow. SimWorks 공식 스토어(store.sim-works.com)에서 Nissen 상품 이미지 주소가 `.github/image-candidates.txt`로 커밋됩니다. (스토어 구조가 Shopify가 아니면 실패하니, 그때는 URL을 직접 모읍니다.)
2. 쓸 이미지를 골라 `.github/image-manifest.txt`에 `<URL> <저장 경로>` 형식으로 적고 main에 푸시하면 **Fetch images** 워크플로가 받아서 `images/`에 커밋합니다. 필요한 경로 목록은 매니페스트 파일 상단 주석에 있습니다.
3. 이미 받은 파일은 건너뛰므로, 교체할 때는 해당 파일을 지우거나 새 파일명으로 추가합니다.
4. 루비워크샵에서 직접 촬영한 사진(케이블 교체 작업 컷 등)은 같은 경로에 바로 커밋하면 됩니다.

## 문구 수정과 번역
1. `index.src.html`의 한국어 문구를 고칩니다.
2. `python3 tools/build.py` 로 한국어 페이지를 만들고, `python3 i18n/extract.py` 로 `ko.json`을 갱신합니다.
3. 새로 생기거나 바뀐 한국어 문장을 `en.json` · `ja.json`에 같은 키로 추가합니다. HTML 태그는 원문과 똑같이 유지합니다.
4. 다시 `python3 tools/build.py` 를 실행하면 번역되지 않은 문장이 있을 때 목록으로 알려줍니다.

빌드에는 `beautifulsoup4`가 필요합니다 (`pip install beautifulsoup4`).

## 검수 필요
- 브랜드 소개와 사양은 공개된 SimWorks by Nissen 자료와 판매처 정보(70년 가까운 역사, 직기 스프링에서 출발, SP31 SUS304 31가닥 워링턴·플라스마 도금, 아우터 지름 5mm/4mm, 16색, 헤리티지 프렌치·이탈리안)를 바탕으로 썼습니다. 공개 전에 수입 자료와 맞춰 확인합니다.
- 샵 링크 `https://rubiworkshop.com/nissen` 가 실제 카테고리 주소인지 확인합니다.
- 니센 코리아 인스타그램 계정이 생기면 푸터 Links와 JSON-LD `sameAs`에 추가합니다.

## 링크
- 헤더 SHOP, 각 제품의 "루비워크샵에서 보기" 버튼: `https://rubiworkshop.com/nissen`
- 거래처 문의: 루비서플라이 02-516-8465, 카카오톡 채널 `https://pf.kakao.com/_NFnBj/chat`
- 푸터 SimWorks: `https://sim-works.com/`
