# Seoul Yoga & Tea — Landing Page

영어 요가 클래스(한강공원, 토요일 아침)를 위한 SEO 최적화 정적 랜딩 페이지.
도메인 구입 없이 **GitHub Pages**로 무료 배포 가능. 구글이 클래스 정보를 리치 결과로
띄울 수 있도록 **JSON-LD 구조화 데이터**(SportsActivityLocation + 반복 Event)가 들어있습니다.

---

## 1. 먼저 채워야 할 자리 (`YOUR_HANDLE` 전부 교체)

`index.html` 안의 `YOUR_HANDLE`을 본인 것으로 바꾸세요. (에디터에서 전체 찾기·바꾸기 추천)

| 자리표시자 | 바꿀 값 | 들어가는 곳 |
|---|---|---|
| `YOUR_HANDLE.github.io` | 본인 깃헙 페이지 주소 | canonical, OG, 구조화 데이터 |
| `instagram.com/YOUR_HANDLE` | 인스타 핸들 | 소셜 링크 |
| `threads.net/@YOUR_HANDLE` | 스레드 핸들 | 소셜 링크 |
| `litt.ly/YOUR_HANDLE` | 본인 Litly 주소 | "Book a Spot" 예약 버튼 |

> 좌표(`37.5448 / 126.8983`)는 양화한강공원 대략값입니다. 정확한 집결지로 바꾸려면
> 구글맵에서 핀 우클릭 → 나오는 위도/경도를 `latitude`/`longitude`에 넣으세요.
> 클래스 시간이 60분이 아니면 `endDate`/`endTime`도 함께 수정하세요.

## 2. 사진 넣기

`images/` 폴더의 `README.md` 참고. 핵심은 `og-image.jpg`(공유 썸네일) 한 장은 꼭 넣기.

## 3. GitHub Pages로 배포 (도메인 불필요)

```bash
cd /Users/jade/Projects/Doban/rocket
git init
git add .
git commit -m "Seoul Yoga & Tea landing page"

# 깃헙에서 빈 레포 'seoul-park-yoga' 생성 후:
git remote add origin https://github.com/<당신아이디>/seoul-park-yoga.git
git branch -M main
git push -u origin main
```

그다음 레포 페이지에서: **Settings → Pages → Source: `main` 브랜치 / `/root` → Save**
1~2분 뒤 `https://<당신아이디>.github.io/seoul-park-yoga/` 에서 라이브.

> 주소를 `https://<아이디>.github.io/` (서브폴더 없이)로 깔끔하게 쓰려면
> 레포 이름을 `<당신아이디>.github.io` 로 만드세요.

## 4. 배포 후 SEO 마무리 (중요)

1. **구글 서치 콘솔**(search.google.com/search-console)에 사이트 등록 → 색인 요청.
   소셜에만 의존하지 말고 여기서 직접 구글에 "내 페이지 봐줘"라고 알리는 단계.
2. **구조화 데이터 검증**: https://search.google.com/test/rich-results 에 URL 넣고
   Event/LocalBusiness가 인식되는지 확인.
3. **구글 비즈니스 프로필** 등록 시 웹사이트 칸에 이 주소를 넣어 연결.
4. 인스타·스레드·Litly 바이오 링크를 전부 이 페이지로 모으기.

---

## 5. 계절이 바뀔 때 (장소 갱신)

봄·가을(야외 한강) ↔ 여름·겨울(마포 실내)이 바뀌면 두 군데만 손보면 됩니다:
- `index.html`의 JSON-LD `Event` → `location`(Place의 name/address/geo)을 현재 시즌 장소로
- 마포 실내 주소가 확정되면 `addressLocality: "Mapo-gu"`에 `streetAddress` 추가 +
  `geo` 좌표 넣기 (구글맵 핀 우클릭 → 위도/경도)

> 브랜드명(Seoul Yoga & Tea)·요일·가격은 그대로 두고 **장소만** 갱신하면 됩니다.
> 클래스가 늘면 `Event` 블록을 복사해 추가하면 여러 클래스도 구조화 데이터로 표현돼요.

## 파일 구조
```
index.html      ← 본문 + 모든 메타/구조화 데이터
styles.css      ← 디자인 (새벽 한강 테마)
images/         ← 사진
.nojekyll       ← GitHub Pages가 폴더를 그대로 서빙하도록
```
