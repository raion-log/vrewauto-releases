# 수강생 안내 사이트

GitHub Pages 로 서비스한다. **주소·소스·수정 권한이 전부 `raion-log` 계정에 있다.**
옛 담당자 계정 Netlify 에서 2026-09-06 옮겨 왔다.

```
docs/
  index.html            브루만 있는 버전 안내  ← update/vrew-only.json 을 읽는다
  with-capcut/          캡컷 포함 버전 안내    ← update/with-capcut.json 을 읽는다
  v210/                 옛 주소 리다이렉트 (즐겨찾기 보호)
  sayong/  flow/  update-v205/   사용법·흐름·구버전 안내
  img/                  이미지
```

## 판 번호와 다운로드 주소를 고치는 법

**HTML 을 고치지 않는다.** 두 페이지 모두 `update/*.json` 을 읽어 판 번호·다운로드 주소·
파일 이름을 그린다. 채널 파일 한 줄만 고치고 push 하면 페이지가 따라 바뀐다.

```jsonc
// update/with-capcut.json
{
  "version": "2.1.2",
  "windows_url": "https://github.com/raion-log/vrewauto-releases/releases/download/v2.1.2/...",
  "mac_url": "..."
}
```

- 값이 **비어 있으면 페이지가 덮어쓰지 않는다.** 아직 안 올린 판을 가리켜 링크가 죽는 일이 없다
- 채널을 못 읽어도 HTML 에 적힌 기본값으로 계속 동작한다 (2026-08-12 채널 차단 전례)
- ★`version` 은 설치파일을 릴리즈에 올리고 안내를 보낸 **뒤에** 올린다

## 두 페이지를 절대 섞지 않는다

브루만 쓰는 사람이 캡컷 포함판을 받으면 기존 설치를 덮어쓴다. 설치 식별자가 같기 때문이다.
2026-08-05 와 2026-09-04 에 실제로 그 사고가 났다.
