# GSA Infoteam 약관 모음

GSA Infoteam에서 운영하는 서비스들의 이용약관, 개인정보처리방침 등 문서가 모여있습니다.

- [https://terms.gistory.me/](https://terms.gistory.me/): 목록 페이지
- [https://terms.gistory.me/account/index.json](https://terms.gistory.me/account/index.json): 최신 약관 목록 (json)
- [https://terms.gistory.me/account/tos/260201](https://terms.gistory.me/account/tos/260201): 약관 보기
- [https://terms.gistory.me/embedded/account/tos/260201](https://terms.gistory.me/embedded/account/tos/260201): 임베딩 버전

## 앱에 임베드하기

임베딩 버전은 배경이 투명하고 헤더가 없어서 앱 화면 안에 그대로 넣을 수 있습니다.

### 다크 모드

앱의 테마 설정을 `theme` 쿼리로 넘기면 됩니다. iframe에 따로 CSS를 줄 필요는 없습니다.

```tsx
const { theme } = useTheme(); // 'light' | 'dark' | 'system'

<iframe
  src={`https://terms.gistory.me/embedded/ziggle/tos/250302/?theme=${theme}`}
  sandbox="allow-scripts"
/>
```

| 값 | 동작 |
| --- | --- |
| (없음), `light` | 라이트 |
| `dark` | 다크 |
| `system` | OS 설정 |
| `auto` | iframe 요소의 `color-scheme`. 테마를 바꿔도 다시 불러오지 않아야 할 때 씁니다. |

- 테마는 스크립트로 고르므로 `sandbox`에는 `allow-scripts`가 있어야 합니다.

## 서비스 추가하기

`content/<서비스>/` 폴더를 만들고 `_index.md`에 메인 페이지에 보일 이름, 색, 아이콘을 적습니다. 셋 중 하나라도 없으면 빌드가 실패합니다.

```yaml
---
title: "팟쥐"
params:
  color: "#418501"
  icon: "P"
---
```

약관은 `content/<서비스>/<privacy|tos>/<YYMMDD>.md`에 둡니다. 파일 이름이 버전입니다.
