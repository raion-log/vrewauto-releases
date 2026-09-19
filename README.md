# VrewAuto 배포

VrewAuto 의 **설치파일·업데이트 채널·수강생 안내 사이트**를 두는 공개 저장소다.
제품 소스는 비공개 저장소 `raion-log/vrewauto` 에 있다. 관리자는 `raion-log`.

판은 **하나**다(2026-09-19). 브루만 쓰는 사람도 같은 설치파일을 받는다.

## 왜 저장소를 나눴나

설치파일이 200MB급이다. 공개 저장소의 Releases 는 대역폭 제한이 없고 로그인 없이 받을 수 있다.
비공개 Releases 는 다운로드에 로그인이 필요해 수강생 배포에 쓸 수 없다. (결정 D-003)

## 구성

```
update/
  with-capcut.json   업데이트 채널 — version·notes·force·windows_url·mac_url·published_at
  common.json        공용 — 공지(notices)와 이미지 생성 주소(imggen_url)
docs/                수강생 안내 사이트 (GitHub Pages) — docs/README.md
Releases
  v<판>              판별 설치파일 (윈도우 exe · 맥 dmg)
  gpu-pack-v1        GPU 가속팩 DLL 2개 — 판과 무관. 판 릴리즈를 정리해도 지우지 않는다
```

공용 파일에 판 번호나 설치파일 주소를 넣지 않는다.

채널 주소: `https://raw.githubusercontent.com/raion-log/vrewauto-releases/main/update/with-capcut.json`

## 배포 순서 (지키지 않으면 사고가 난다)

1. 릴리즈를 만들고 설치파일을 올린다. 로그인 없이 받아지는지 확인한다
2. 안내를 보낸다
3. **마지막에** `update/with-capcut.json` 의 `version`·주소를 채운다

3번을 먼저 하면 전 사용자에게 받을 것이 없는 업데이트 알림이 간다.
이 저장소에는 유료 워크플로가 없다(Pages 자동 배포뿐). 태그·릴리즈를 만들어도 크레딧을 쓰지 않는다.

상세 절차는 소스 저장소의 `docs/RELEASE.md`.
