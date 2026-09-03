# VrewAuto 배포

VrewAuto 자동배치의 **설치파일과 업데이트 채널**을 두는 공개 저장소다.
제품 소스는 비공개 저장소 `raion-log/vrewauto`에 있다.

**두 판이 있다.** 캡컷까지 쓰는 「캡컷 포함 버전」과 브루만 쓰는 「브루만 있는 버전」이다.
같은 소스에서 빌드 옵션으로 갈린다. (예전 문서에서는 각각 신규반·통합반이라 불렀다.)

## 왜 저장소를 나눴나

설치파일이 200MB급이다. 공개 저장소의 Releases는 대역폭 제한이 없고 로그인 없이 받을 수 있다.
비공개 Releases는 다운로드에 로그인이 필요해 수강생 배포에 쓸 수 없다. (결정 D-003)

## 구성

```
update/
  with-capcut.json  캡컷 포함 버전 업데이트 채널 — version·notes·force·windows_url·mac_url
  vrew-only.json    브루만 있는 버전 업데이트 채널 — 같은 구조
  common.json       두 버전 공용 — 공지(notices)와 이미지 생성 주소(imggen_url)
releases/         GitHub Releases — 태그별 설치파일
```

공용 파일에 판 번호나 설치파일 주소를 넣지 않는다. 버전을 가르는 값은 버전별 파일에만 둔다.

**★두 채널은 절대 섞지 않는다.** 한 채널을 두 버전이 읽으면 반대편 설치파일을 받게 되고,
두 버전의 설치 식별자가 같아 서로를 덮어쓴다. 2026-08-05와 2026-08-12에 같은 사고가 두 번 났다.

## 채널 주소

두 가지를 쓸 수 있다. 파일은 같다.

```
https://raw.githubusercontent.com/raion-log/vrewauto-releases/main/update/with-capcut.json
https://raion-log.github.io/vrewauto-releases/update/new.json   (Pages 켠 뒤)
```

## 배포 순서 (지키지 않으면 사고가 난다)

1. 릴리즈를 먼저 만들고 설치파일을 올린다
2. 안내를 갱신한다
3. **마지막에** `update/*.json`의 `version`을 올린다

3번을 먼저 하면 전 사용자에게 받을 것이 없는 업데이트 알림이 간다.

상세 절차는 소스 저장소의 `docs/RELEASE.md`.
