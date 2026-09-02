# VrewAuto 배포

VrewAuto 자동배치의 **설치파일과 업데이트 채널**을 두는 공개 저장소다.
제품 소스는 비공개 저장소 `raion-log/vrewauto`에 있다.

## 왜 저장소를 나눴나

설치파일이 200MB급이다. 공개 저장소의 Releases는 대역폭 제한이 없고 로그인 없이 받을 수 있다.
비공개 Releases는 다운로드에 로그인이 필요해 수강생 배포에 쓸 수 없다. (결정 D-003)

## 구성

```
update/
  new.json        신규반(캡컷 포함) 업데이트 채널
  classic.json    통합반(브루 전용) 업데이트 채널
releases/         GitHub Releases — 태그별 설치파일
```

**★두 채널은 절대 섞지 않는다.** 한 채널을 두 계보가 읽으면 반대편 설치파일을 받게 되고,
두 계보의 설치 식별자가 같아 서로를 덮어쓴다. 2026-08-05와 2026-08-12에 같은 사고가 두 번 났다.

## 채널 주소

두 가지를 쓸 수 있다. 파일은 같다.

```
https://raw.githubusercontent.com/raion-log/vrewauto-releases/main/update/new.json
https://raion-log.github.io/vrewauto-releases/update/new.json   (Pages 켠 뒤)
```

## 배포 순서 (지키지 않으면 사고가 난다)

1. 릴리즈를 먼저 만들고 설치파일을 올린다
2. 안내를 갱신한다
3. **마지막에** `update/*.json`의 `version`을 올린다

3번을 먼저 하면 전 사용자에게 받을 것이 없는 업데이트 알림이 간다.

상세 절차는 소스 저장소의 `docs/RELEASE.md`.
