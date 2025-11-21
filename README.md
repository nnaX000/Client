# 🗓️ 모임 — 새내기들을 위한 시간·장소 조율 및 장소 추천 웹서비스 (프론트엔드 레포)
<br>

## 프로젝트 소개

대학생 새내기들이 약속을 정할 때 겪는 **시간 조율과 장소 선정의 번거로움**을 해결하고 학교 근처 맛집을 추천하기 위한 웹서비스입니다.  

![Next.js](https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white)
![AWS EC2](https://img.shields.io/badge/AWS%20EC2-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![AWS S3](https://img.shields.io/badge/AWS%20S3-569A31?style=for-the-badge&logo=amazons3&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

---

# 💡 담당한 개발 내용

> Frontend 리드로서 **장소 추천 페이지[place]** 핵심 UI/UX 전반을 구현했습니다.

<br>

## 1. 플레이스 추천 카드 **무한 스크롤** 구현
- 스크롤 위치 직접 계산 후 **90% 도달 시 자동 추가 로딩**
- BottomSheet 상태(`expanded` / `middle`)에 따라 fetch 동작 분기
- `fetchCategoryData()` 또는 `fetchFilteredCategoryData()` 실행
- `Set`을 활용해 **카드 id 중복 제거 처리**

---

## 2. 카카오 맵 기반 **사용자 위치 탐색 및 설정**
- `getCurrentLocation()`으로 브라우저 **Geolocation API** 호출
- 현재 위치 클릭 시 `selectedLocation`에 저장 후 지도 중심 이동
- 검색창 텍스트를 자동으로 현재 위치명으로 설정
- Kakao Map Ref를 통한 지도 제어

---

## 3. 사용자 정보 호출 및 동적 반영
- `fetchUserInformation()` 호출하여 유저 닉네임을 가져와 문구에 반영
- 유저 기반 맞춤 텍스트 적용

---

## 4. 탭 별 **필터 버튼 동적 생성 및 상태 반영**
- 탭에 맞는 필터 데이터를 서버에서 받아와 렌더링
- 선택된 필터는 `filtersRef.current`에서 상태 관리
- 선택 여부에 따라 스타일 동적 반영
- 필터 변경 시 `fetchFilteredCategoryData()` 자동 호출

---

## 5. 좋아요 기능 (토글 및 개수 실시간 반영)
- `fetchLikeCount()`를 통해 카드의 좋아요 수 실시간 갱신
- `useLikeSystem()` 커스텀 훅으로 기능 캡슐화 → 재사용성 증가
- 다른 카테고리/컴포넌트에서도 동일 로직 활용 가능

---

## 6. BottomSheet 드래그 기반 상태 변화
- `touchstart`, `touchmove`, `touchend` 이벤트 기반으로 deltaY 계산
- 드래그 위치에 따라 `collapsed`, `middle`, `expanded` 상태 전환
- 상태에 따른 BottomSheet 높이 및 **카카오맵 margin-bottom 자동 조정**
- 터치 + 마우스 모두 지원하는 드래그 처리

---

## 개발 기간
2024.12 ~ 2025.02

---

## 팀 구성 및 역할

| 이름 | 역할 |
|------|------|
| **김나영** 외 4명 | 프론트엔드 |
| **우태경** | 백엔드 |
| **정규원** | 백엔드 |

---

## 결과물
실제 사업화까지 진행하였습니다.
