# 타로카드 서비스 — Design System Guide (DESIGN.md)

> **신비로운 식물학 양피지 수첩에 깃든 타로**
>
> Botanical & Celestial Sketchbook dipped in Honey
>
> 크림빛 종이, 딥 인디고 잉크, 꿀빛 천체와 식물 라인아트로 만드는 가벼운 모바일 타로 경험.

## 0. 기준과 적용 범위

- **갱신일**: 2026-11-19.
- **시각 기준**: [타로 디자인 팩 — Figma](https://www.figma.com/design/o7pHCrCLyHdeS3C86j69NA?node-id=2-2)의 현재 화면 실측값.
- **제품 기준**: `TARO_01_PRD.md`, `TARO_02_기능명세서.md`, `TARO_03_유저플로우.md`, `TARO_04_와이어프레임.md`. 로그인 없음, 개인정보 비저장, 메이저 아르카나 22장·정방향 한 장, 해석 최대 3줄·90자 원칙은 변경하지 않는다.
- **사용자 확인**: 현재 화면의 실측값을 기준으로 정리하며, 없는 상태·규칙은 기존 가이드를 유지한다.
- **등록 현황**: 현재 Figma에는 화면 9개와 공유 이미지 1개가 있으며, 등록된 메인 컴포넌트·컴포넌트 세트·로컬 색/텍스트/효과 스타일·변수 컬렉션은 없다. 아래 컴포넌트 이름과 CSS 토큰은 화면에서 추출한 **구현용 명명 규칙**이지, 이미 배포된 Figma 라이브러리의 이름이나 키가 아니다.
- **표기**: `[실측]`은 현재 화면에서 확인한 값, `[기존 유지]`는 화면에 없는 기존 규칙이다. 별도 표기가 없는 화면 크기·색·서체·간격 표는 실측 기준이다. 시안에 없는 동작을 구현 완료된 것으로 해석하지 않는다.

### 주요 변경점

| 항목 | 이전 가이드 | 현재 기준 |
|---|---|---|
| 모바일 기준 | 390~430px | **375 × 852px** 기준 시안; 확장 폭 상한 430px는 기존 유지 |
| 한글 제목·본문·UI | Pretendard/Inter, 제목에 Bebas Neue 혼용 | **Noto Sans KR** Regular 400 / Bold 700 |
| 영문 강조 | 여러 대체 서체 병렬 표기 | 카드 영문명 Bebas Neue, 감성 영문 Caveat, 브랜드 Inter |
| 주제 배치 | '2열'과 `grid-cols-3` 설명 충돌 | **3열 × 2행**, 가로 8px / 세로 10px |
| 버튼 | 일반 높이 위주 | 시작 54px / 뽑기 52px / 저장·공유 48px / 보조 40px |
| 개인정보 안내 | 테두리 있음, 패딩 14px | **테두리 없음**, 샌드 바탕, 입력 화면 패딩 12px |
| 결과 카드 | 문서 내 그림자·배경 설명 불일치 | 흰색 4:5 카드, 인디고 9% 그림자; 저장본 그림자 없음 |
| 예외 상태 | 토스트·모달 간략 안내 | 입력 전·날짜 오류·저장/복사 토스트·저장/복사 바텀시트 명세 추가 |

---

## 1. 디자인 원칙

1. **따뜻하고 친근한 신비로움**: 기존 Pa'lais 스타일 레퍼런스의 아티잔 감성을 이어 간다. 보라색·검은 벨벳의 무거운 오컬트 테마가 아닌, 크림색 수첩과 식물도감의 인상을 유지한다.
2. **가입 없이 약 1분**: 시작 → 정보·주제 입력 → 카드 한 장의 결과. 저장·공유는 결과 확인 후 선택하는 부가 행동이다.
3. **인디고로 구조, 따뜻한 색으로 강조**: 텍스트·주요 CTA·선택 상태는 딥 인디고. 골드·오렌지·민트는 삽화·워시·보조선에 사용하고 주요 버튼 전체를 채우지 않는다.
4. **개인정보 투명성**: 이름·생년월일·전공은 화면 메모리에서만 사용한다. 서버 전송, localStorage, 쿠키, 분석 도구 전송과 결과 이력을 만들지 않는다. 새로 고침·창 닫기·[처음으로] 시 삭제한다.
5. **짧고 열려 있는 해석**: 카드 × 주제 + 별자리 + 전공 계열(입력·분류 가능 시)의 최대 3줄·90자. 건강·재물에 단정적인 예언을 하지 않으며 오락용 안내를 유지한다.

## 2. 색상과 효과

### 2.1 화면에서 사용하는 색

| 구현 토큰 | 값 | 역할 |
|---|---|---|
| `deep-indigo` / `primary` | `#234386` | 제목·주요 CTA·선택 주제·아이콘·토스트 |
| `cream-paper` / `background` | `#fbf9f6` | 페이지·바텀시트 바탕 |
| `pure-white` / `card` | `#ffffff` | 입력 필드·결과 카드·미선택 주제·공유 메시지 박스 |
| `ink-black` / `foreground` | `#1a1a1a` | 본문·입력값·미선택 주제 텍스트 |
| `muted-foreground` | `#666666` | 부제·보조 설명·오락용 안내 |
| `placeholder` | `#777777` | 입력 전 플레이스홀더 |
| `warm-sand` / `border` / `input` | `#d2b68c` | 입력창·미선택 주제·보조 버튼 테두리 |
| `privacy-surface` | `#f3eee5` | 개인정보 안내·별자리 배지 |
| `secondary` | `#f0ebe1` | 다시 뽑기 버튼 바탕 |
| `honey-gold` | `#ffc400` | 태양·별빛·시작 화면 워시 |
| `burnt-orange` | `#ed7328` | 결과 공유 테두리·텍스트, 삽화 포인트 |
| `mint-sage` | `#a2d3a6` | 시작 화면 워시·식물 삽화 포인트 |
| `destructive` | `#d9383a` | 잘못된 날짜 필드 테두리 |
| `error-text` | `#bd3031` | 날짜 오류 설명 |
| `overlay` | `rgba(24,38,74,0.32)` | 바텀시트 뒤 화면 딤 |

시작 화면의 골드·민트 워시 도형 불투명도는 각각 **48%**다. 색상 자체를 연한 HEX로 바꾸지 않는다. 일러스트 내부의 세부 색은 원본 벡터를 기준으로 하며, 모든 경로의 색을 UI 토큰으로 승격하지 않는다.

### 2.2 그림자·선·모서리

| 대상 | 기준 |
|---|---|
| 시작 카드 뒷면 그림자 | `-6px 12px 22px rgba(35,67,134,0.16)` |
| 결과 카드 그림자 | `-8px 12px 32px rgba(35,67,134,0.09)` |
| 결과 카드 테두리 | 1px, `rgba(35,67,134,0.13)` |
| 일반 입력·주제·보조 버튼 테두리 | 1px, Warm Sand |
| 결과 공유 / 날짜 오류 테두리 | 1.5px, 각각 Burnt Orange / Destructive |
| 버튼 / 주제 / 배지 반경 | 32px / 20px / 16px |
| 입력 / 결과 카드·개인정보·토스트 반경 | 8px / 12px |
| 바텀시트 반경 | 위쪽 두 모서리 24px, 아래쪽 0 |

### 2.3 화면에 없는 색·효과 — 기존 유지

`sky-blue: #6aa8dc`, `muted: #e8e2d5`, `soft-shadow: rgba(0,0,0,0.08)`, `shadow-blob: 0 16px 32px rgba(255,196,0,0.15)`는 기존 확장용 정의를 유지한다. 현재 주요 화면에 쓰인 것으로 간주하지 않으며 결과 카드의 실측 그림자를 대체하지 않는다.

호버용 `#1b356d`(주요 버튼), `#e4dcce`(보조 버튼), 오렌지 10% 워시, 인디고 5% 워시도 `[기존 유지]`다. 포커스 링은 딥 인디고이며 오렌지보다 우선한다.

## 3. 타이포그래피

### 3.1 서체 역할

- **Noto Sans KR Regular 400 / Bold 700**: 한글 제목, 본문, 폼, 버튼, 안내. 한글 제목에 Bebas Neue를 지정하지 않는다.
- **Bebas Neue Regular 400**: `XIX THE SUN`처럼 영문·로마 숫자로 된 카드 명칭.
- **Caveat Regular 400**: `The stars whisper to you`, `A little light for your day` 감성 영문.
- **Inter Medium 500**: `TARO` 브랜드, 영문 브랜드 레이블, 일부 장식 문자.
- `[기존 유지]` Noto Sans KR 사용이 불가능한 환경의 대체 순서는 Pretendard → Inter → system-ui. 기존 영문 대체안 Oswald, hwt-artz, Delivery Note와 스크립트 대체안 Nanum Pen Script, Dancing Script, 레이블 대체안 ITC Avant Garde Std는 예비안으로만 남긴다. 대체 적용 시 줄바꿈과 한글 글리프를 확인한다.

### 3.2 실측 타입 스케일

자간은 별도 기재가 없으면 **0**이다. 150% 행간은 Figma에서 픽셀 반올림되어 표시될 수 있다.

| 역할 / 구현 토큰 | 서체·굵기 | 크기 / 행간 | 자간 |
|---|---|---|---|
| 시작 제목 `hero` | Noto Sans KR 700 | 40px / 150% | 0 |
| 입력 제목·카드 한글명 `title` | Noto Sans KR 700 | 23px / 150% | 0 |
| 결과 화면 제목 `result-heading` | Noto Sans KR 700 | 22px / 150% | 0 |
| 바텀시트 제목 `sheet-heading` | Noto Sans KR 700 | 20px / 160% | 0 |
| 주제 섹션 제목 `subheading` | Noto Sans KR 700 | 18px / 150% | 0 |
| 카드 영문명 `card-en` | Bebas Neue 400 | 18px / 150% | 1.4px |
| 브랜드 `brand` | Inter 500 | 17px / 150% | 0 |
| 시작 본문·입력값 `input` | Noto Sans KR 400 | 16px / 150% | 0 |
| 해석 `reading` | Noto Sans KR 400 | 15px / 24px | -0.2px |
| 시작·뽑기 버튼 `cta` | Noto Sans KR 700 | 15px / 150% | 0 |
| 시트 복귀 버튼 `sheet-button` | Noto Sans KR 700 | 14px / 160% | 0 |
| 필드 레이블 | Noto Sans KR 700 | 13px / 150% | 0 |
| 주제·결과 주요 액션·일반 설명 | Noto Sans KR 400 | 13px / 150% | 0 |
| 바텀시트 설명 | Noto Sans KR 400 | 13px / 160% | 0 |
| 직접 복사할 메시지 | Noto Sans KR 400 | 13px / 23px | 0 |
| 내비게이션·결과 개인화 제목·보조 액션 | Noto Sans KR 400 | 12px / 150% | 0 |
| 개인정보 안내 `privacy` | Noto Sans KR 400 | 11px / 18px | 0 |
| 단계·힌트·별자리·보조 고지 | Noto Sans KR 400 | 11px / 150% | 0 |
| 결과 오락용 안내·워터마크·글자 수 | Noto Sans KR 400 | 10px / 150% | 0 |
| 브랜드 영문 레이블 | Inter 500 | 9px / 150% | 1.5px |
| 시작 감성 영문 `script-hero` | Caveat 400 | 25px / 150% | 0 |
| 결과 감성 영문 `script-result` | Caveat 400 | 23px / 150% | 0 |

시트 하단 보조 고지는 11px / 160%다. 장식용 별 문자는 Inter 25px·32px 등이며 본문 타입 스케일에 포함하지 않는다. 이전 가이드의 UI 전체 넓은 자간 0.12~0.25em, 제목 105% 행간은 현재 화면의 기본 규칙이 아니다.

9~11px는 현재 시안의 보조 정보 실측값이지 접근성 충족을 보증하는 최소 크기가 아니다. 확대·대체 서체·작은 화면에서 읽기 어려우면 콘텐츠를 자르거나 본문·입력 글자를 줄이지 말고 스크롤과 재배치를 우선 검토한다. 입력값 16px 이상 원칙은 유지한다.

## 4. 레이아웃과 간격

### 4.1 모바일 기준

- 기준 화면: **375 × 852px**. 좌우 여백 각각 **24px**, 기본 콘텐츠 폭 **327px**.
- 화면 상하 기본 여백은 24px, 상단 내비게이션/브랜드 영역 높이는 44px.
- 실제 모바일 웹에서는 852px를 고정 높이로 강제하거나 넘친 내용을 숨기지 않는다. 콘텐츠와 키보드·브라우저 높이에 따라 세로 스크롤을 허용한다.
- `[기존 유지]` 페이지는 중앙 정렬, 최대 폭 430px, 최소 높이 뷰포트 높이. 375px 외 별도 시안이나 브레이크포인트는 없다. 넓은 화면에서도 모바일 구성을 늘리며 새 데스크톱 레이아웃을 추정하지 않는다.
- 안전 영역 대응은 구현 시 별도로 확인한다. 시안 상하 24px를 운영체제 상태바·홈 인디케이터 크기로 해석하지 않는다.

### 4.2 의미별 실측 간격

| 위치 | 간격 / 패딩 |
|---|---|
| 시작 제목 ↔ 감성 문구 | 5px |
| 시작 액션 영역 내부 | 18px |
| 입력 제목 ↔ 부제 | 7px |
| 입력 그룹 사이 | 16px |
| 레이블 ↔ 필드 / 레이블 ↔ 힌트 | 6px / 6px |
| 필드 내부 | 좌우 14px, 내용 ↔ 아이콘 8px |
| 주제 섹션 | 위 22px / 아래 20px, 제목·행 사이 10px |
| 주제 칩 | 열 간격 8px, 행 간격 10px, 아이콘 ↔ 글자 6px |
| 결과 제목 ↔ 감성 문구 | 4px |
| 결과 카드 내부 | 위·좌우 16px / 아래 14px, 항목 사이 7px |
| 결과 액션 영역 | 위 20px, 내부 세로 10px, 버튼 열 사이 9px |
| 개인정보 안내 — 입력 | 사방 12px, 아이콘 ↔ 글자 9px |
| 개인정보 안내 — 결과 | 상하 10px / 좌우 12px, 아이콘 ↔ 글자 8px |
| 토스트 | 상하 15px / 좌우 17px, 아이콘 ↔ 글자 10px |
| 바텀시트 | 위 12px / 좌우 24px / 아래 28px, 항목 사이 14px |
| 수동 복사 메시지 박스 | 사방 16px |

이는 등록된 spacing 변수 스케일이 아니라 **역할별 측정값**이다. 7px·9px·17px처럼 화면에 존재하는 값을 임의로 4px 배수로 치환하지 않는다. 축소 미리보기와 1080px 출력물의 비례 확대값을 별도의 간격 토큰으로 만들지 않는다.

## 5. 컴포넌트 명세

아래 명칭은 shadcn/ui·Tailwind 기반 구현에서 사용할 역할명이다. 기존 `default`, `outline`, `secondary`, `ghost`, `topic` 변형 구분을 유지하되 실측값으로 맞춘다.

### 5.1 Button

| 용도 | 변형 | 폭 / 높이 | 글자 | 바탕·선 |
|---|---|---|---|---|
| 타로 시작 | `default` | 콘텐츠 전체 / 54px | 15px Bold | 인디고 / 선 없음 |
| 카드 한 장 뽑기 | `default` | 콘텐츠 전체 / 52px | 15px Bold | 인디고 / 선 없음 |
| 이미지 저장 | `default` | 결과 첫 행의 한 열 / 48px | 13px Regular | 인디고 / 선 없음 |
| 결과 공유 | `outline` | 결과 첫 행의 한 열 / 48px | 13px Regular | 투명 / 오렌지 1.5px |
| 다시 뽑기 | `secondary` | 결과 둘째 행의 한 열 / 40px | 12px Regular | `#f0ebe1` / 샌드 1px |
| 처음으로 | `ghost` | 결과 둘째 행의 한 열 / 40px | 12px Regular | 투명 / 선 없음 |
| 결과로 돌아가기 | `default` | 시트 콘텐츠 전체 / 48px | 14px Bold | 인디고 / 선 없음 |

모두 반경 32px. 인디고 바탕의 글자·아이콘은 흰색, outline은 오렌지, secondary/ghost는 인디고다. 결과 버튼의 아이콘은 18px, 글자와 7px 간격. 시작 버튼의 화살표와 문구 간격은 12px, 뽑기 버튼의 별과 문구 간격은 8px다.

- **비활성 `[실측]`**: 버튼 전체 opacity 40%. 이름·유효한 생년월일·주제가 충족되지 않거나 날짜 오류가 있으면 뽑기 비활성.
- **호버·누름 `[기존 유지]`**: 주요 버튼 `#1b356d`, secondary `#e4dcce`, outline 오렌지 10%, ghost 인디고 5%. 전환 200ms, 누를 때 scale 0.95, 비활성 입력 차단.
- **일반 확장 크기 `[기존 유지]`**: 기존 `sm` 36px, `default` 48px, `lg` 56px, 아이콘 버튼 40px는 아직 배치되지 않은 용도에만 사용한다. 화면별 54px·52px·48px·40px를 덮어쓰지 않는다.

### 5.2 InputField

- 327 × 48px 기준, 흰색, 반경 8px, 샌드 1px 선, 좌우 패딩 14px.
- 레이블 13px Bold, 힌트 11px, 입력/플레이스홀더 16px, 글자 수 10px.
- 이름: 닉네임 허용, 최대 10자, 빈 값 안내 `닉네임을 입력해 주세요`; `지민`은 예시 입력값이지 플레이스홀더가 아니다.
- 생년월일: 빈 값 `YYYY . MM . DD`, 값 예시 `2004 . 08 . 03`. 별자리 계산에만 사용. 달력 아이콘 20px.
- 전공: 선택, 빈 값 `예: 경영학과`. 인문·사회·경영·자연·공학·예체능으로 분류하고 미입력/분류 불가이면 전공 해석 줄을 생략한다.
- 오류: 날짜 선 `#d9383a` 1.5px, 아래 `날짜를 다시 확인해 주세요`를 12px·`#bd3031`로 표시. 색만으로 오류를 전달하지 않는다.
- 포커스 `[기존 유지]`: 2px 딥 인디고 링, 투명 테두리. 실제 날짜 검증과 날짜 피커 지원을 유지한다. `2004 . 02 . 30`은 오류 상태 예시이며 유효값이 아니다.

### 5.3 TopicChip

- 3열 × 2행: 커리어·재물·연애 / 건강·학업·종합. 한 번에 하나 선택.
- 폭 `(콘텐츠 폭 - 16px) / 3`, 375px 화면에서 약 103.67px. 높이 39px, 반경 20px.
- 미선택: 흰색·샌드 1px 선·Ink Black 글자·인디고 아이콘.
- 선택: 인디고 바탕·선, 흰색 글자·아이콘. 글자 13px, 아이콘 15px, 사이 6px.
- 주제 아이콘은 서류가방·지갑·하트·잎·책·별의 라인 벡터다. 이전 문서의 이모지 표기를 그대로 UI 자산으로 사용하지 않는다.

### 5.4 PrivacyCallout

`#f3eee5` 바탕, 반경 12px, **테두리 없음**. 입력 화면은 패딩 12px·아이콘 20px, 결과는 상하 10px/좌우 12px·아이콘 18px. 글자는 인디고 11px / 18px.

> 입력한 이름 · 생년월일 · 전공은 해석을 만드는 데만 쓰고, 서버로 보내거나 저장하지 않아요. 창을 닫거나 [처음으로]를 누르면 바로 지워져요.

### 5.5 TarotResultCard

- 화면 크기 **327 × 408.75px**, **4:5**. 흰색, 반경 12px, 인디고 13%의 1px 선, 9% 인디고 그림자.
- 내부는 위에서부터 개인화 제목 → 삽화 → 영문명 → 한글명·별자리 → 해석 → 오락용 고지·서비스명.
- 개인화 제목 `지민님의 타로 · 커리어`: 12px. 태양 삽화 영역: **145 × 154px**.
- 영문명 `XIX THE SUN`: Bebas Neue 18px, 자간 1.4px. 한글명 `태양`: Noto Sans KR Bold 23px.
- 별자리 배지: 11px, `#f3eee5`, 반경 16px, 상하 4px/좌우 9px.
- 해석: 15px / 24px, 자간 -0.2px, 가운데 정렬, 최대 3줄·90자. 세 줄을 서로 다른 길이의 장문 문단으로 늘리지 않는다.
- 하단 오락용 안내와 `오늘의 타로 · tarot.app`: 10px, 각각 Muted / Indigo.
- 생년월일과 전공 **원문은 카드에 넣지 않는다**. 전공 계열로 만든 해석 문장은 포함할 수 있다.

### 5.6 Toast

- 폭 327px, 인디고 바탕, 반경 12px, 흰색 완료 아이콘 19px·글자 13px.
- 패딩 상하 15px/좌우 17px, 간격 10px. 한 줄 저장 안내 높이 50px, 두 줄 복사 안내 70px는 콘텐츠에 따른 결과값이다.
- 저장 완료: `이미지를 저장했어요`.
- 자동 복사 완료: `결과를 복사했어요. 원하는 앱에 붙여 넣어 주세요`.
- `[기존 유지]` 3초 후 페이드아웃. 시안은 정지 상태이며 타이머 구현을 증명하지 않는다. 실측 y=675px는 852px 높이의 예시 위치일 뿐 모든 기기의 고정 좌표가 아니다.

### 5.7 FallbackBottomSheet

- 전체 화면 딤 `rgba(24,38,74,0.32)`. 시트는 화면 하단, 크림 바탕, 위 모서리 24px.
- 패딩 위 12px/좌우 24px/아래 28px, 항목 간격 14px. 핸들 36 × 4px, 제목 20px Bold, 닫기 아이콘 22px.
- 저장 대체: 제목 `나만의 카드를 간직해요`, 안내 `이 브라우저에서는 바로 저장하기가 어려워요. 이미지를 길게 눌러 저장해 주세요.`, **271 × 338.75px**의 4:5 이미지 미리보기, 닉네임·별자리 포함 고지, [결과로 돌아가기].
- 복사 대체: 제목 `직접 복사해서 공유해요`, 안내 `자동 복사를 지원하지 않는 브라우저예요. 아래 글을 길게 눌러 복사해 주세요.`, 직접 선택할 메시지, 개인정보 없는 링크 안내, [결과로 돌아가기].
- 메시지 박스: 흰색·샌드 1px 선·반경 12px·패딩 16px, 글자 13px / 23px.
- 저장 시트 592.75px, 복사 시트 495px는 예시 콘텐츠의 실측 높이. 고정 높이로 강제하지 말고 짧은 기기에서 내부 스크롤을 허용한다. 저장 대체 미리보기는 최종 PNG를 보여 주며 사용자 정보 입력 화면 전체를 캡처하지 않는다.

## 6. 화면과 상태 매핑

| ID | Figma 기준 | 내용 |
|---|---|---|
| S-01 | [시작](https://www.figma.com/design/o7pHCrCLyHdeS3C86j69NA?node-id=2-2) | 브랜드, `오늘의 타로`, 감성 영문, 카드 뒷면, 본문, 시작 CTA, 오락용·비저장 안내 |
| S-02 | [입력 완료](https://www.figma.com/design/o7pHCrCLyHdeS3C86j69NA?node-id=2-7) | 뒤로가기, `01 / 02`, 이름·생년월일·선택 전공, 주제, 개인정보, 활성 뽑기 |
| S-02a | [입력 전](https://www.figma.com/design/o7pHCrCLyHdeS3C86j69NA?node-id=2-8449) | 빈 필드, 주제 미선택, 비활성 뽑기 |
| S-02b | [날짜 오류](https://www.figma.com/design/o7pHCrCLyHdeS3C86j69NA?node-id=2-8522) | 날짜 오류 문구·선, 비활성 뽑기 |
| S-03 | [결과](https://www.figma.com/design/o7pHCrCLyHdeS3C86j69NA?node-id=2-14) | `02 / 02`, 결과 제목·감성 영문, 카드, 공개 정보 안내, 액션 2행, 개인정보 |
| S-03a | [저장 완료](https://www.figma.com/design/o7pHCrCLyHdeS3C86j69NA?node-id=2-8596) | 결과 + 저장 토스트 |
| S-03b | [저장 대체](https://www.figma.com/design/o7pHCrCLyHdeS3C86j69NA?node-id=2-8837) | 길게 눌러 저장하는 바텀시트 |
| S-03c | [자동 복사 완료](https://www.figma.com/design/o7pHCrCLyHdeS3C86j69NA?node-id=2-8690) | 결과 + 복사 토스트 |
| S-03d | [수동 복사](https://www.figma.com/design/o7pHCrCLyHdeS3C86j69NA?node-id=2-8990) | 직접 선택할 메시지가 있는 바텀시트 |
| Export | [공유 이미지](https://www.figma.com/design/o7pHCrCLyHdeS3C86j69NA?node-id=2-8784) | 1080 × 1350 PNG 기준 |

시작 비주얼 영역 높이는 344px, 카드 뒷면은 196 × 286px에 -7° 기울기다. 제목은 `오늘의 타로`, 감성 영문은 `The stars whisper to you`, 본문은 `내 정보를 넣고 카드 한 장으로 / 나만의 해석을 받아 봐요`로 역할이 분리된다. 본문 자체를 스크립트 서체로 바꾸지 않는다.

결과 제목은 `오늘, 당신에게 온 카드`, 감성 영문은 `A little light for your day`. 카드 아래에 `저장·공유할 때 닉네임과 별자리가 포함돼요.`를 표시한다. 첫 액션 행은 저장/공유, 둘째는 다시 뽑기/처음으로다.

## 7. 흐름·동작 — 기존 유지

- 타로 시작 → S-02. 입력·실제 날짜·주제가 유효할 때만 뽑기 가능.
- 메이저 아르카나 22장 중 무작위 한 장, 정방향. 서버·AI 실시간 해석 대신 앱에 미리 넣은 문구를 조합한다.
- 다시 뽑기 → 입력 정보를 유지한 채 S-02에서 주제 선택부터. 처음으로 → 정보 모두 삭제 후 S-01. 공유 링크를 받은 사람도 S-01부터 시작한다.
- 이미지 저장 성공 → 토스트. 다운로드 제한 → 이미지 저장 대체 시트.
- 기기 공유 메뉴 지원 → 이미지와 글 공유; 완료/취소 후 결과 유지. 미지원 → 글 자동 복사; 복사 성공 → 토스트, 복사도 실패 → 직접 선택할 메시지.
- 카드 플립은 **0.8초**(1초 이내), perspective 1000px, rotateY 180°, easing `cubic-bezier(0.34, 1.56, 0.64, 1)`. 현재 정지 시안에서 새 모션 값은 추출하지 않았다.

```css
/* 기존 모션 규칙 유지: 현재 화면에 애니메이션이 연결됐다는 의미는 아니다. */
.flip-card { perspective: 1000px; }
.flip-card-inner {
  transition: transform 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
  transform-style: preserve-3d;
}
.flip-card.flipped .flip-card-inner { transform: rotateY(180deg); }
.flip-card-front, .flip-card-back { backface-visibility: hidden; }
.flip-card-back { transform: rotateY(180deg); }
```

## 8. 저장 이미지와 공유 문구

### 8.1 PNG 출력

- **1080 × 1350px, 4:5**. 화면의 327 × 408.75px 결과 카드를 `1080 / 327`배로 비례 확대한다. 글자·간격·모서리도 함께 확대하며 출력 폭만 늘리거나 카드 내용을 재배치하지 않는다.
- 현재 저장본은 **흰색 카드 바탕**, 얇은 인디고 선, **바깥 그림자 없음**이다. 기존 설명의 크림 바탕·추가 골드/민트 블롭을 저장본에 임의로 추가하지 않는다.
- 포함: 이름/닉네임, 주제, 카드 삽화·영문명·한글명, 별자리, 최대 3줄 해석, `※ 오락용 타로 해석입니다`, `오늘의 타로 · tarot.app`.
- 제외: 생년월일 원문, 전공 원문, 입력 폼, 액션 버튼, 개인정보 안내 박스. 전공 기반 해석 문장은 원문 입력값과 구분한다.
- 4:5는 피드형 세로 이미지다. **9:16 스토리 전체 화면 규격과 동일하지 않다.** 스토리에서도 이미지로 공유할 수 있으나 꽉 찬 9:16 이미지로 표기하지 않는다.

### 8.2 공유 텍스트

수동 복사 시안에 맞춰 장식 이모지·인용부호 없이 아래 내용을 사용한다. 전공 미입력/분류 불가 시 세 번째 해석 줄은 생략하며 빈 자리 문구를 넣지 않는다.

```text
{이름}님의 타로 · {주제}
{카드 한글 이름} · {별자리}

{해석 1줄}
{해석 2줄}
{해석 3줄 — 있을 때만}

※ 오락용 타로 해석입니다
나도 한 장 뽑기 → {시작 화면 URL}
```

`https://tarot.app`과 워터마크 도메인은 현재 시안·기존 가이드의 예시를 유지한 것이며, 실제 서비스 도메인 소유·배포 여부를 보증하지 않는다. 운영 배포 시 확정된 시작 URL과 서비스 워터마크로 함께 교체한다. 링크에 이름·생년월일·전공·결과를 쿼리나 경로로 넣지 않는다.

## 9. 구현용 토큰 예시 — Tailwind CSS v4

다음은 실측값·기존 유지 규칙·구현용 의미 매핑을 함께 담은 예시다. 현재 Figma에 이 이름의 변수가 등록되어 있다는 뜻이 아니다. `primary`, `background`, `input`, `accent` 등의 별칭은 구현용 매핑이며 등록된 Figma 토큰의 증거가 아니다. shadcn/ui를 쓰면 이 의미 토큰에 연결하며, 기본 크기·기본 폰트를 그대로 두지 않는다.

```css
@import "tailwindcss";

@theme {
  --color-deep-indigo: #234386;
  --color-honey-gold: #ffc400;
  --color-burnt-orange: #ed7328;
  --color-warm-sand: #d2b68c;
  --color-mint-sage: #a2d3a6;
  --color-ink-black: #1a1a1a;
  --color-pure-white: #ffffff;
  --color-cream-paper: #fbf9f6;
  --color-background: #fbf9f6;
  --color-foreground: #1a1a1a;
  --color-primary: #234386;
  --color-primary-foreground: #ffffff;
  --color-secondary: #f0ebe1;
  --color-secondary-foreground: #234386;
  --color-muted-foreground: #666666;
  --color-placeholder: #777777;
  --color-privacy-surface: #f3eee5;
  --color-border: #d2b68c;
  --color-input: #d2b68c;
  --color-ring: #234386;
  --color-card: #ffffff;
  --color-card-foreground: #1a1a1a;
  --color-accent: #ffc400;
  --color-accent-foreground: #234386;
  --color-destructive: #d9383a;
  --color-destructive-foreground: #ffffff;
  --color-error-text: #bd3031;
  --color-overlay: rgba(24, 38, 74, 0.32);

  /* 기존 확장 토큰 유지 — 현재 주요 화면의 실측 사용값과 구분 */
  --color-sky-blue: #6aa8dc;
  --color-muted: #e8e2d5;
  --color-soft-shadow: rgba(0, 0, 0, 0.08);
  --shadow-blob: 0 16px 32px rgba(255, 196, 0, 0.15);

  /* 첫 서체는 실측, 대체 서체는 기존 유지 규칙 */
  --font-sans: "Noto Sans KR", "Pretendard", "Inter", system-ui, sans-serif;
  --font-display: "Bebas Neue", "Oswald", sans-serif;
  --font-script: "Caveat", "Nanum Pen Script", "Dancing Script", cursive;
  --font-brand: "Inter", system-ui, sans-serif;
  --radius-input: 8px;
  --radius-card: 12px;
  --radius-badge: 16px;
  --radius-topic: 20px;
  --radius-sheet: 24px;
  --radius-button: 32px;
  --shadow-tarot-card: -8px 12px 32px rgba(35, 67, 134, 0.09);
  --shadow-tarot-back: -6px 12px 22px rgba(35, 67, 134, 0.16);
}

:root {
  --page-inset: 24px;
  --field-gap: 16px;
  --field-label-gap: 6px;
  --topic-column-gap: 8px;
  --topic-row-gap: 10px;
  --action-column-gap: 9px;
}

body {
  margin: 0;
  background: var(--color-background);
  color: var(--color-foreground);
  font-family: var(--font-sans);
  -webkit-font-smoothing: antialiased;
}
.taro-page {
  /* 최대 폭 430px는 기존 유지, 유동 최소 높이는 웹 구현 대응 */
  width: 100%; max-width: 430px; min-height: 100dvh;
  margin-inline: auto; padding-block: 24px;
}
.taro-region { padding-inline: var(--page-inset); }
.taro-reading { font: 400 15px/24px var(--font-sans); letter-spacing: -0.2px; }
.taro-topics {
  display: grid; grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: var(--topic-row-gap) var(--topic-column-gap);
}
.taro-input {
  box-sizing: border-box; width: 100%; height: 48px; padding-inline: 14px;
  border: 1px solid var(--color-input); border-radius: 8px;
  background: #fff; color: var(--color-foreground);
  font: 400 16px/1.5 var(--font-sans);
}
.taro-input::placeholder { color: var(--color-placeholder); }
.taro-input[aria-invalid="true"] { border: 1.5px solid var(--color-destructive); }
/* 기존 포커스 규칙 유지 */
.taro-input:focus-visible {
  outline: 2px solid var(--color-ring); border-color: transparent;
}
.taro-result-card {
  box-sizing: border-box; width: 100%; aspect-ratio: 4 / 5;
  padding: 16px 16px 14px; border-radius: 12px;
  border: 1px solid rgba(35, 67, 134, 0.13);
  background: #fff; box-shadow: var(--shadow-tarot-card);
}
.taro-button {
  display: inline-flex; align-items: center; justify-content: center;
  border-radius: 32px; letter-spacing: 0;
  /* 아래 전환·누름·비활성 입력 차단은 기존 유지 규칙 */
  transition: background-color 200ms, transform 200ms;
}
.taro-button:active { transform: scale(0.95); }
.taro-button:disabled { opacity: 0.4; pointer-events: none; }
/* 크기와 글꼴은 Button 표에 따라 용도별로 적용한다. */
```

필수 서체의 웹 로딩·라이선스를 배포 환경에서 확인한다. 위 예시는 토큰 연결용이며 완성된 UI 구현이 아니다. 4:5 카드에서 콘텐츠가 넘치면 해석 길이와 서체 로딩을 먼저 확인하고, 작은 글자로 억지 축소하거나 정보를 잘라내지 않는다.

## 10. 인계 체크리스트

- [ ] 375px에서 좌우 24px, 3열 주제, 용도별 버튼 높이와 Noto Sans KR 적용을 확인한다.
- [ ] 빈 입력·잘못된 실제 날짜·선택 전 주제에서 뽑기가 비활성인지 확인한다.
- [ ] 해석이 3줄·90자 이내이며 전공 미입력/분류 불가 시 3번째 줄이 없는지 확인한다.
- [ ] 저장/공유에 생년월일·전공 원문이 없고 닉네임·별자리 포함 안내가 보이는지 확인한다.
- [ ] PNG 1080 × 1350, 흰색 4:5 카드, 그림자 제외, 서비스명·오락용 고지를 확인한다.
- [ ] 저장 제한 → 길게 눌러 저장, 공유 미지원 → 자동 복사, 복사 실패 → 수동 선택을 확인한다.
- [ ] 처음으로·새로 고침·창 닫기 후 개인정보가 남지 않고 공유 링크가 시작 화면으로 가는지 확인한다.
- [ ] 서체 대체·텍스트 확대·짧은 화면·키보드·안전 영역에서 콘텐츠가 잘리지 않는지 확인한다.
- [ ] 작은 보조 글자, 색 대비, 키보드 포커스, 아이콘 접근성 이름과 터치 영역을 별도로 검토한다. 정지 시안만으로 접근성을 통과한 것으로 보지 않는다.
- [ ] 전체 22장 카드 자산과 사용 권한, 실제 서비스 URL/워터마크를 출시 전에 확정한다. 현재 팩에서 확인되는 대표 그림은 카드 뒷면과 태양이며 22장 전체 자산이 준비된 것으로 간주하지 않는다.

이 갱신은 디자인 가이드만 변경한다. Figma의 컴포넌트화·변수 등록, 나머지 카드 삽화 제작, 애플리케이션 구현 및 PRD의 미정 항목 확정을 대신하지 않는다.
