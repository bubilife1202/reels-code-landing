# 릴스코드 (Reels Code) 랜딩페이지

조회수를 매출로 바꾸는 릴스 설계 전문가 - 1인 기업·소상공인을 위한 릴스 마케팅 컨설팅

## 📋 주요 기능

### ✅ 완료된 최적화 항목

1. **SEO 최적화**
   - Open Graph 메타태그 (Facebook, KakaoTalk 공유 최적화)
   - Twitter Card 메타태그
   - 검색 엔진 최적화 메타 description
   - 키워드 최적화
   - Favicon 추가 (💡 이모지)

2. **Google Analytics 4 준비**
   - GA4 이벤트 추적 코드 준비됨
   - CTA 클릭 추적 설정
   - 체크리스트 다운로드 추적 설정
   - PDF 저장 이벤트 추적 설정

3. **전환율 최적화 (CRO)**
   - 성과 사례 섹션 추가
   - 전문성 강화 문구 개선 (CVR, Insights, A/B 테스트 용어)
   - Instagram 연계 섹션 추가
   - 긴급성 요소 추가 ("이번 주 한정 5자리 남음")
   - 리스크 제거 요소 추가 ("무료 상담", "강매 없음")

4. **사용자 경험 (UX)**
   - 스크롤 애니메이션 추가
   - 모바일 반응형 디자인
   - 빠른 로딩 속도 (외부 라이브러리 없음)

5. **프로젝트 구조 정리**
   - .gitignore 추가 (Python 파일 제외)
   - 상대 경로 링크 수정

---

## 🚀 Google Analytics 설정 방법

현재 GA4 코드는 **주석 처리**되어 있습니다. 활성화하려면:

### 1단계: Google Analytics 계정 생성

1. [Google Analytics](https://analytics.google.com/) 접속
2. "측정 시작" 클릭
3. 계정 이름: "릴스코드" (원하는 이름)
4. 속성 이름: "릴스코드 랜딩페이지"
5. 웹 스트림 추가: `https://reelscode.netlify.app`
6. **측정 ID 복사** (형식: `G-XXXXXXXXXX`)

### 2단계: 코드 활성화

#### index.html 수정 (28-74번 줄)
```html
<!-- 주석 제거: 아래 라인 삭제 -->
<!--

<!-- 코드 활성화 후 -->
<script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
<script>
    window.dataLayer = window.dataLayer || [];
    ...
</script>

<!-- 주석 제거: 아래 라인 삭제 -->
-->
```

#### checklist.html 수정 (28-63번 줄)
동일한 방법으로 주석 제거 및 측정 ID 교체

### 3단계: 측정 ID 교체

모든 `G-XXXXXXXXXX`를 실제 측정 ID로 교체:
```bash
# 자동 교체 (Linux/Mac)
sed -i 's/G-XXXXXXXXXX/G-실제측정ID/g' index.html
sed -i 's/G-XXXXXXXXXX/G-실제측정ID/g' checklist.html
```

### 4단계: 배포 및 테스트

1. 변경사항 커밋 및 푸시
2. Netlify 자동 배포 대기 (약 1-2분)
3. Google Analytics 실시간 보고서에서 확인
4. 본인이 페이지 방문 → 실시간 사용자 1명 표시되면 성공!

---

## 📊 추적 가능한 이벤트

Google Analytics 활성화 시 자동으로 추적되는 이벤트:

### index.html
- **카카오톡 CTA 클릭** (`event: 'click'`, `label: 'KakaoTalk CTA'`)
- **Google Form CTA 클릭** (`event: 'click'`, `label: 'Google Form CTA'`)
- **체크리스트 다운로드** (`event: 'click'`, `label: 'Checklist Download'`)

### checklist.html
- **PDF 저장 버튼 클릭** (`event: 'click'`, `label: 'PDF Download'`)
- **메인 페이지로 CTA 클릭** (`event: 'click'`, `label: 'Checklist to Main CTA'`)

---

## 🎨 커스터마이징

### 색상 변경
주요 브랜드 색상 (`index.html` CSS):
```css
/* 메인 색상 (골드) */
#f5a962
#d4a574

/* 보조 색상 */
#333 (다크 그레이)
#f9f9f9 (라이트 그레이)
```

### 성과 수치 변경
`index.html` 572-584번 줄:
```html
<div class="stat-number">300%+</div> <!-- 원하는 수치로 변경 -->
```

### 케이스 스터디 수정
`index.html` 587-608번 줄:
실제 고객 사례로 교체

---

## 📱 SNS 링크 확인

현재 설정된 링크:
- Instagram: `https://www.instagram.com/reels_code_official/`
- KakaoTalk: `https://open.kakao.com/o/sTYC6FOh`
- Google Form: `https://forms.gle/xns3B9wCou7tdDpf7`

**중요:** 이 링크들이 실제로 작동하는지 정기적으로 확인하세요!

---

## 🔧 로컬 개발

```bash
# 저장소 클론
git clone <repository-url>

# 로컬 서버 실행 (Python 3)
python -m http.server 8000

# 브라우저에서 접속
http://localhost:8000
```

---

## 📦 배포

### Netlify 배포 (권장)
1. GitHub 저장소 연결
2. Build settings:
   - Build command: (비워두기)
   - Publish directory: `/`
3. 자동 배포 완료!

### 기타 호스팅
- GitHub Pages
- Vercel
- Cloudflare Pages

모두 정적 HTML이므로 어디든 배포 가능

---

## ✅ 체크리스트: 런칭 전 확인사항

- [ ] Google Analytics 측정 ID 교체 완료
- [ ] GA4 주석 제거 및 활성화
- [ ] Instagram 링크 작동 확인
- [ ] KakaoTalk 오픈채팅 링크 작동 확인
- [ ] Google Form 링크 작동 확인
- [ ] 모바일 디바이스에서 테스트
- [ ] 성과 수치를 실제 데이터로 업데이트
- [ ] 케이스 스터디를 실제 사례로 교체
- [ ] 긴급성 문구 주기적 업데이트 ("이번 주 X자리 남음")

---

## 📈 성과 측정 KPI

Google Analytics에서 주기적으로 확인할 지표:

1. **전환율**
   - 카카오톡 CTA 클릭률: 목표 15%+
   - 체크리스트 다운로드율: 목표 25%+

2. **사용자 행동**
   - 평균 페이지 체류 시간: 목표 2분+
   - 이탈률: 목표 50% 이하

3. **트래픽**
   - 일일 방문자 수
   - 유입 경로 (Instagram, 검색, 직접 방문)

---

## 🐛 문제 해결

### Google Analytics가 작동하지 않을 때
1. 주석(`<!-- -->`)이 제대로 제거되었는지 확인
2. 측정 ID가 올바른지 확인 (`G-`로 시작)
3. 브라우저 개발자 도구 → Console에서 오류 확인
4. AdBlocker 비활성화 후 테스트

### 링크가 작동하지 않을 때
1. URL이 `https://`로 시작하는지 확인
2. KakaoTalk 오픈채팅은 만료될 수 있음 → 새로 생성
3. 모바일에서도 테스트

---

## 📞 문의

프로젝트 관련 문의:
- Instagram: [@reels_code_official](https://www.instagram.com/reels_code_official/)
- KakaoTalk: [오픈채팅 참여](https://open.kakao.com/o/sTYC6FOh)

---

## 📄 라이선스

© 2025 릴스코드. All rights reserved.
