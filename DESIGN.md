# 타로카드 서비스 — Design System Guide (DESIGN.md)

> **"신비로운 식물학 양피지 수첩에 깃든 타로 (Botanical & Celestial Sketchbook dipped in Honey)"**  
> 따뜻한 크림빛 종이 캔버스(`#fbf9f6`), 맑고 깊은 딥 인디고(`#234386`) 잉크의 서체와 천체·식물 세밀화 라인아트, 그리고 꿀빛 골드(`#ffc400`)와 번트 오렌지(`#ed7328`)의 유기적인 블롭(Blob) 형태가 어우러진 현대적 에디토리얼 모바일 타로 서비스입니다.

---

## 1. 개요 및 디자인 철학

본 디자인 시스템은 **[Pa'lais Style Reference]**의 따뜻한 아티잔 핸드메이드 감성을 기반으로, **[타로카드 기획문서(TARO_01~04)]**의 핵심 목표와 사용자 흐름을 모바일 웹 환경에 최적화하여 재구성한 시스템입니다.

### 핵심 디자인 원칙
1. **따뜻하고 친근한 신비로움 (Warm & Cozy Mysticism)**: 차갑고 어두운 오컬트 분위기 대신, 유럽의 오래된 레시피 수첩이나 식물도감을 펼친 듯한 편안하고 따뜻한 크림 페이퍼 바탕에 별과 식물 라인아트를 더해 감성적인 신비감을 전달합니다.
2. **모바일 1분 경험 & 높은 가독성 (1-Minute Mobile Flow)**: 390~430px 모바일 화면에 맞춰 불필요한 시각 요소를 덜어내고, 3줄(90자) 이내의 맞춤 해석과 액션 버튼(32px 필 버튼)이 한눈에 들어오도록 설계합니다.
3. **신뢰와 투명성 (Zero-Data Privacy)**: 입력한 개인정보는 브라우저 메모리 안에서만 사용되고 즉시 소멸한다는 원칙을 부드러운 인디고/샌드 톤의 잠금 아이콘과 정갈한 텍스트로 안심시킵니다.
4. **인스타 스토리 최적화 카드 (1080×1350 Shareable Canvas)**: S-03 결과 화면의 타로 카드는 세로 4:5(1080×1350) 비율로 설계되어, 캡처하거나 [이미지 저장] 시 왜곡 없이 감성적인 결과물로 저장됩니다.

---

## 2. 디자인 토큰 — 색상 (Colors)

시스템은 **딥 인디고(`#234386`)**를 유일한 쿨톤이자 브랜드의 구조적 닻(Anchor)으로 사용합니다. 타이포그래피, 주요 버튼, 테두리, 라인아트의 기본색은 딥 인디고가 담당하며, 그 외의 에너지는 따뜻한 꿀빛 골드, 오렌지, 민트 세이지가 유기적인 블롭 형태로 전달합니다.

| 토큰명 | HEX / OKLCH | Tailwind 클래스 | 역할 및 가이드 |
|---|---|---|---|
| **Deep Indigo** | `#234386` | `bg-deep-indigo`, `text-deep-indigo` | **Primary Brand**: 헤드라인, 링크, 활성화된 주요 CTA 버튼(필), 라인아트 획, 선택된 토픽 칩. 전체 시스템의 구조적 신뢰감을 부여하는 핵심 컬러 |
| **Honey Gold** | `#ffc400` | `bg-honey-gold`, `text-honey-gold` | **Celestial Accent**: 타로 카드의 별빛, 태양, 배경 유기적 블롭, 강조 뱃지. 면 채움 버튼으로는 쓰지 않고 그래픽 포인트로만 활용 |
| **Burnt Orange** | `#ed7328` | `border-burnt-orange`, `text-burnt-orange` | **Secondary Accent**: 아웃라인 2차 버튼 테두리, 알림 배지, 하이라이트 문구, 인터랙티브 포커스 |
| **Sky Blue** | `#6aa8dc` | `text-sky-blue`, `bg-sky-blue` | **Illustration Wash**: 별자리 기호, 보조 천체 라인아트, 신비로운 안개형 블롭 |
| **Warm Sand** | `#d2b68c` | `bg-warm-sand`, `border-warm-sand` | **Paper Neutral**: 캔버스와 카드 사이를 이어주는 부드러운 디바이더, 인풋 테두리, 보조 칩 배경 |
| **Mint Sage** | `#a2d3a6` | `bg-mint-sage` | **Botanical Accent**: 힐링, 건강 주제 칩 포인트, 식물 모티브 블롭 워시 |
| **Ink Black** | `#1a1a1a` | `text-ink-black` | **Body Text**: 본문 해석 텍스트, 얇은 구분선(1px), 폼 입력 필드 텍스트 |
| **Pure White** | `#ffffff` | `bg-pure-white` | **Card Surface**: 타로 결과 카드 표면, 인풋 박스 배경, 버튼 내부 텍스트 |
| **Cream Paper** | `#fbf9f6` | `bg-cream-paper` | **Page Canvas**: 전체 모바일 웹 배경. 화면이 아닌 실제 고급 종이 수첩을 보는 듯한 아날로그 질감 형성 |
| **Soft Shadow** | `rgba(0,0,0,0.08)` | `shadow-soft` | **Card Elevation**: 카드 모서리를 띄우는 비대칭 자연광 그림자 |

---

## 3. 디자인 토큰 — 타이포그래피 (Typography)

타이포그래피는 **강렬한 압축형 헤드라인**, **친근하고 시적인 스크립트 서체**, **정갈한 현대적 본문 고딕(Pretendard/Inter)**, 그리고 **넓은 자간(0.13~0.25em)의 레이블** 4가지 목소리로 나뉩니다.

### 서체 구성
- **Display Heading**: `Bebas Neue`, `Oswald` (대체: `hwt-artz`, `Delivery Note`)
  - 용도: "오늘의 타로", 카드 명칭("XIX THE SUN", "태양"), 섹션 대제목
  - 특징: 굵고 압축된 대문자 영문/숫자, 타이트한 행간(0.9~1.1)
- **Script Accent**: `Caveat`, `Nanum Pen Script` (대체: `Dancing Script`)
  - 용도: 감성 문구, "The stars whisper to you", "나만을 위한 별의 조언"
  - 특징: 손글씨 뉘앙스, 약간의 기울기
- **Body & UI**: `Pretendard`, `Inter`, `system-ui`
  - 용도: 맞춤 해석 3줄(90자 이내), 폼 라벨, 폼 인풋 텍스트, 개인정보 안내문
  - 특징: 14~16px, 높은 가독성의 1.6 행간
- **Eyebrow & Label**: `ITC Avant Garde Std`, `Pretendard`
  - 용도: 별자리 표시("♌ 사자자리"), 토픽 뱃지, 버튼 텍스트
  - 특징: 대문자, 극단적으로 넓은 자간 (`tracking-[0.15em]~[0.25em]`)

### Type Scale (모바일 최적화)

| 토큰 | 크기 | 행간 | 자간 | 적용 위치 (Wireframe 매핑) |
|---|---|---|---|---|
| `--text-hero` | 40px | 1.05 | 1.2px | S-01 "🔮 오늘의 타로" 메인 타이틀 |
| `--text-card-title` | 24px | 1.15 | 0.8px | S-03 "XIX 태양", 카드 한글/영문 이름 |
| `--text-subheading` | 18px | 1.3 | 0.4px | S-02 "나에 대해 알려 주세요", "어떤 주제가 궁금한가요?" |
| `--text-script` | 20px | 1.2 | 0 | 감성 카피 및 부제 (Caveat) |
| `--text-body` | 15px | 1.6 | -0.2px | S-03 맞춤 해석 3줄 (최대 90자 문장) |
| `--text-caption` | 12px | 1.5 | 0.5px | 오락용 안내, 개인정보 미저장 안내문 |
| `--text-button` | 14px | 1.0 | 0.12em | CTA 버튼 ("타로 시작", "카드 한 장 뽑기", "이미지 저장") |
| `--text-badge` | 11px | 1.0 | 0.2em | 별자리 뱃지, 상단 카테고리 태그 |

---

## 4. 컴포넌트 규칙 (shadcn/ui & Tailwind v4)

### 4.1 버튼 (Button) — `shadcn buttonVariants`

버튼은 **32px 필(Pill) 형태**를 표준으로 사용하며, 카드의 소프트 사각 모서리(8px)와 대비를 이룹니다.

```tsx
// buttonVariants 설정 가이드
const buttonVariants = cva(
  "inline-flex items-center justify-center font-medium transition-all duration-200 active:scale-95 disabled:opacity-40 disabled:pointer-events-none rounded-[32px]",
  {
    variants: {
      variant: {
        // [F-1, F-3] 주요 CTA: 타로 시작, 카드 한 장 뽑기
        default: "bg-[#234386] text-white hover:bg-[#1b356d] shadow-sm px-8 py-4 text-[15px] tracking-[0.08em] font-semibold",
        // [F-5, F-6] 2차 액션: 결과 공유, 이미지 저장
        outline: "border-2 border-[#ed7328] text-[#ed7328] hover:bg-[#ed7328]/10 bg-transparent px-6 py-3.5 text-[14px] tracking-[0.05em]",
        // [F-7] 보조 액션: 다시 뽑기, 처음으로
        secondary: "bg-[#f0ebe1] text-[#234386] hover:bg-[#e4dcce] border border-[#d2b68c]/60 px-5 py-3 text-[13px]",
        // 토픽 선택 칩 버튼 (S-02 6개 주제)
        topic: "border border-[#d2b68c] bg-white text-[#1a1a1a] data-[state=checked]:bg-[#234386] data-[state=checked]:text-white data-[state=checked]:border-[#234386] rounded-[20px] py-2.5 px-4 text-[14px]",
        ghost: "hover:bg-[#234386]/5 text-[#234386] underline-offset-4 hover:underline text-[13px]",
      },
      size: {
        default: "h-12 px-6",
        sm: "h-9 px-4 text-xs",
        lg: "h-14 px-8 text-base",
        icon: "h-10 w-10 rounded-full",
      },
    },
    defaultVariants: {
      variant: "default",
      size: "default",
    },
  }
)
```

### 4.2 타로 결과 카드 (Tarot Result Card) & 뒤집기 효과 (F-3, F-4)

- **형태 및 재질**: Pure White(`#ffffff`) 서피스, `rounded-[12px]`, 미세한 헤어라인 테두리(`border border-[#234386]/10`) 및 부드러운 비대칭 음영(`box-shadow: -8px 12px 32px rgba(35,67,134,0.08)`).
- **이미지 규격 (F-5)**: 가로 세로 4:5 비율 (인스타그램 스토리 및 피드 최적 규격인 1080×1350 기준).
- **뒤집기 효과 (F-3)**: 1초 이내(0.8초)의 부드러운 3D 플립 애니메이션 (`perspective: 1000px`, `rotateY(180deg)`).

```css
/* 카드 플립 애니메이션 */
.flip-card {
  perspective: 1000px;
}
.flip-card-inner {
  transition: transform 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
  transform-style: preserve-3d;
}
.flip-card.flipped .flip-card-inner {
  transform: rotateY(180deg);
}
.flip-card-front, .flip-card-back {
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
}
.flip-card-back {
  transform: rotateY(180deg);
}
```

### 4.3 폼 입력 필드 (Input) — S-02 (F-2)

- **디자인**: Pure White 인풋 필드, 8px 코너 라운딩(`rounded-[8px]`), 부드러운 모래빛 테두리(`border-[#d2b68c]`).
- **포커스 상태**: 딥 인디고 링(`focus:ring-2 focus:ring-[#234386] focus:border-transparent`).
- **모바일 필수 대응**: iOS 사파리 자동 확대 방지를 위해 글자 크기는 `16px` 이상 유지.

### 4.4 개인정보 안내 및 알림 박스 (Privacy Callout) — F-2, F-4

- **스타일**: 부드러운 양피지 샌드 배경(`bg-[#f3eee5]`), 얇은 딥 인디고 테두리(`border border-[#234386]/20`), 라운드 `rounded-[12px]`, 패딩 `p-3.5`.
- **아이콘**: 🔒 미니멀 인디고 라인 자물쇠.
- **문구**: "입력한 이름 · 생년월일 · 전공은 해석을 만드는 데만 쓰고 저장하지 않아요. 창을 닫거나 [처음으로]를 누르면 바로 지워져요." (Caption 12px)

### 4.5 토스트 & 모달 (Toast / Modal) — F-5, F-6 상태 처리

- **이미지 저장 성공 시**: "이미지를 저장했어요" (딥 인디고 바텀 토스트, 3초 후 페이드아웃).
- **인앱 브라우저 다운로드 제한 시**: 생성된 1080×1350 이미지를 모달로 띄우고 "이미지를 길게 눌러 저장해 주세요" 안내.
- **공유 메뉴 미지원 환경**: 클립보드 자동 복사 실행 후 "결과를 복사했어요. 원하는 앱에 붙여 넣어 주세요" 토스트 표출.

---

## 5. 화면별 디자인 명세 (S-01 ~ S-03)

```
[모바일 뷰포트 레이아웃 기준: max-w-[430px] mx-auto min-h-screen bg-[#fbf9f6] text-[#1a1a1a]]
```

### S-01 시작 화면 (F-1)
- **헤더**: 미니멀 엠블럼 또는 나침반/달 식물 모티브 라인아트.
- **중앙 비주얼**: 타로 카드 뒷면 일러스트 (딥 인디고 바탕에 골드 천체 기하학 문양). 카드 주변에 부드러운 꿀빛(`Honey Gold`) 오가닉 블롭 배경 워시.
- **타이틀**:
  - `Bebas Neue` 40px: "🔮 오늘의 타로"
  - `Caveat` 20px: "내 정보를 넣고 카드 한 장으로 나만의 해석을 받아 봐요"
- **CTA 버튼**: `[타로 시작]` (32px 필, Deep Indigo 배경, 화이트 텍스트, full width).
- **푸터 안내**: "※ 오락용 타로 · 정보는 저장 안 해요" (12px Caption, Muted).

### S-02 내 정보 & 주제 선택 화면 (F-2)
- **상단 내비게이션**: `← 뒤로가기` (처음 화면으로 복귀).
- **헤딩**: "나에 대해 알려 주세요" (22px Semibold Deep Indigo).
- **입력 폼 영역**:
  - **이름 (닉네임 OK)**: 10자 제한 인풋, 플레이스홀더 "지민".
  - **생년월일**: `YYYY . MM . DD` 형태 (실제 유효 날짜 검증, 날짜 피커 지원).
  - **전공 (선택)**: 플레이스홀더 "경영학과" (인문/사회/경영/자연/공학/예체능 자동 매핑).
- **주제 선택 (Topic Chips - 6종)**:
  - 2열 그리드 배치 (`grid grid-cols-3 gap-2.5`)
  - `[💼 커리어]`, `[💰 재물]`, `[💕 연애]`, `[🌿 건강]`, `[📚 학업]`, `[✨ 종합]`
  - 미선택 시 화이트 카드 / 선택 시 Deep Indigo 솔리드 배경 + 화이트 텍스트 전환.
- **보안 배지**: 🔒 개인정보 미저장 원칙 배너 (크림 샌드 배경).
- **CTA 버튼**: `[카드 한 장 뽑기]` (이름 + 생년월일 + 주제 3가지 충족 시 인디고 활성화, 미충족 시 비활성화 `opacity-40`).

### S-03 맞춤 해석 결과 화면 (F-4 ~ F-7)
- **중앙 타로 결과 카드 (1080×1350 비율 카드 컨테이너)**:
  - 상단: `지민님의 타로 · 커리어` (Eyebrow 13px, Deep Indigo)
  - 중앙: 카드 일러스트 프레임 (예: XIX 태양 카드) + 플립 모션
  - 명칭: `XIX 태양 · ♌ 사자자리` (18px Bold)
  - 맞춤 해석 3줄 (총 90자 이내, 15px, 자간 -0.2px, 행간 1.6):
    - 1줄 (카드×주제): "준비한 것을 드러낼 때예요."
    - 2줄 (별자리): "사자자리의 자신감이 무기가 돼요."
    - 3줄 (전공 계열): "경영학도다운 기획력이 빛나요."
  - 하단 고지: "※ 오락용 타로 해석입니다" (11px, Muted)
- **액션 버튼 그리드 (4종)**:
  - 1행: `[ 📥 이미지 저장 ]` (Primary Indigo) + `[ 🔗 결과 공유 ]` (Outline Burnt Orange)
  - 2행: `[ 🔄 다시 뽑기 ]` (Secondary Sand) + `[ 🏠 처음으로 ]` (Ghost text)
- **하단 안내**: "🔒 정보는 저장되지 않아요. [처음으로]를 누르면 바로 지워져요."

---

## 6. 이미지 저장(1080×1350) 및 공유 메시지 규격

### 6.1 저장 이미지 렌더링 규격 (F-5)
- **크기**: 1080px × 1350px (PNG, 4:5 인스타그램 피드/스토리 비율).
- **캔버스 바탕**: `#fbf9f6` 크림 페이퍼 질감 + 상하단 유기적 골드/민트 블롭 오버레이.
- **포함 요소**:
  - 사용자 이름 & 선택 주제 (예: "지민님의 커리어 타로")
  - 메이저 아르카나 카드 일러스트 & 명칭 (예: "XIX THE SUN 태양")
  - 생년월일 기반 별자리 기호 및 명칭 (예: "♌ 사자자리")
  - 3줄 맞춤 해석 텍스트
  - "※ 오락용 타로 해석입니다"
  - 워터마크 브랜딩: "오늘의 타로 · tarot.app"
  - *(주의: 개인정보 보호를 위해 생년월일 원문 및 전공 원문은 절대 이미지에 포함하지 않음)*

### 6.2 결과 공유 메시지 텍스트 규격 (F-6)
```text
🔮 {이름}님의 타로 · {주제}
{카드 이름} · {별자리}

"{해석 1줄}"
"{해석 2줄}"
"{해석 3줄}"

※ 오락용 타로 해석입니다
나도 한 장 뽑기 → https://tarot.app
```

---

## 7. Do's and Don'ts

### ✅ Do
- **딥 인디고(`#234386`)를 유일한 주력 쿨톤으로 사용**: 헤드라인, 링크, 활성 버튼을 딥 인디고로 고정하여 시각적 질서와 고급스러움을 유지합니다.
- **32px 필 버튼과 8~12px 카드의 대비 유지**: 둥근 알약형 버튼과 정갈한 사각 카드의 비례 대비가 손에 쥐는 수첩 같은 촉각적 감성을 줍니다.
- **3줄 해석의 엄격한 길이 제한 준수**: 모바일 한 화면에서 스크롤 없이 카드와 해석이 다 보이도록 90자 이내로 간결하게 배치합니다.
- **개인정보 즉시 폐기 안내 상시 표시**: 사용자가 불안해하지 않도록 입력창 아래와 결과창 아래에 자물쇠 아이콘과 함께 비저장 원칙을 명시합니다.
- **천체·식물 라인아트를 프레임 밖으로 살짝 걸치기**: 카드 테두리나 화면 모서리에 라인아트를 자연스럽게 배치해 손으로 그린 수첩 느낌을 연출합니다.

### ❌ Don't
- **보라색/어두운 검정 벨벳톤의 오컬트 테마 사용 금지**: 대중적이고 산뜻한 캐주얼 모바일 서비스이므로 무거운 점술 앱 느낌을 배제합니다.
- **생년월일(YYYY.MM.DD) 원문을 결과 이미지나 공유 메시지에 노출 금지**: 프라이버시 보호를 위해 오직 '별자리'로만 변환하여 표기합니다.
- **골드(`#ffc400`)나 오렌지(`#ed7328`)로 전체 버튼 면을 채우지 않기**: 따뜻한 컬러들은 블롭 그래픽과 아웃라인 보조선으로만 써야 인디고의 권위와 가독성이 유지됩니다.
- **단정적인 예언 표현 금지**: "취업에 합격합니다", "부자가 됩니다" 대신 "기획력이 빛을 발할 때예요", "지출 우선순위를 점검해 보세요" 등 관점을 열어주는 표현을 씁니다.

---

## 8. 빠른 구현 코드 (Quick Start)

### Tailwind CSS v4 `@theme` (`app.css`)

```css
@import "tailwindcss";

@theme {
  /* Colors */
  --color-deep-indigo: #234386;
  --color-honey-gold: #ffc400;
  --color-burnt-orange: #ed7328;
  --color-sky-blue: #6aa8dc;
  --color-warm-sand: #d2b68c;
  --color-mint-sage: #a2d3a6;
  --color-ink-black: #1a1a1a;
  --color-pure-white: #ffffff;
  --color-cream-paper: #fbf9f6;
  --color-soft-shadow: rgba(0, 0, 0, 0.08);

  /* Semantic Theme Mappings for shadcn */
  --color-background: #fbf9f6;
  --color-foreground: #1a1a1a;
  --color-primary: #234386;
  --color-primary-foreground: #ffffff;
  --color-secondary: #f0ebe1;
  --color-secondary-foreground: #234386;
  --color-muted: #e8e2d5;
  --color-muted-foreground: #666666;
  --color-accent: #ffc400;
  --color-accent-foreground: #234386;
  --color-destructive: #d9383a;
  --color-destructive-foreground: #ffffff;
  --color-border: #d2b68c;
  --color-input: #e2dbce;
  --color-ring: #234386;
  --color-card: #ffffff;
  --color-card-foreground: #1a1a1a;

  /* Fonts */
  --font-display: "Bebas Neue", "Oswald", sans-serif;
  --font-script: "Caveat", cursive;
  --font-sans: "Pretendard", "Inter", -apple-system, BlinkMacSystemFont, system-ui, sans-serif;

  /* Radii */
  --radius-card: 12px;
  --radius-input: 8px;
  --radius-button: 32px;
  --radius-badge: 16px;

  /* Shadows */
  --shadow-tarot-card: -8px 12px 32px rgba(35, 67, 134, 0.09);
  --shadow-blob: 0 16px 32px rgba(255, 196, 0, 0.15);
}

/* Base Body Styles */
body {
  background-color: var(--color-cream-paper);
  color: var(--color-ink-black);
  font-family: var(--font-sans);
  -webkit-font-smoothing: antialiased;
}
```
