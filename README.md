# 잠금화면 문구 만들기

원하는 문구를 넣어 아이폰·갤럭시 잠금화면 배경(PNG)을 만드는 도구.
정적 HTML 한 장. 빌드도 서버도 없고, 모든 렌더링이 브라우저 Canvas에서 일어난다.
입력한 문구는 어디로도 전송되지 않는다.

## 구성

```
index.html    전부 여기 (HTML + CSS + JS)
icon.png      파비콘 / 홈 화면 아이콘
og.png        링크 공유용 미리보기
vercel.json   보안 헤더 + 캐시 정책
```

## 배포 (셋 중 하나)

### 1. Vercel CLI — 제일 빠름

```bash
npm i -g vercel
cd wallpaper-site
vercel          # 첫 배포: 프로젝트 이름을 물어봄 → 그 이름이 주소가 됨
vercel --prod   # 프로덕션 반영
```

Framework Preset을 물으면 **Other**를 고른다. 빌드 명령은 비워둔다.

### 2. GitHub 연동 — 이후 수정이 편함

```bash
git init && git add . && git commit -m "init"
gh repo create wallpaper-maker --public --source=. --push
```

vercel.com → Add New Project → 해당 저장소 Import → Deploy.
이후엔 `git push`만 하면 자동 배포된다.

### 3. 드래그 앤 드롭

vercel.com/new 에서 이 폴더를 통째로 끌어다 놓는다. 계정만 있으면 끝.

## 주소

프로젝트 이름이 곧 주소가 된다. 예: `wallpaper.vercel.app`
이름이 이미 쓰이고 있으면 Vercel이 접미사를 붙이므로,
원하는 주소가 있으면 Settings → Domains 에서 바꾼다.

## 수정

`index.html` 하나만 고치면 된다. 주요 지점:

| 위치 | 내용 |
|---|---|
| `DEVICES` | 기기 프리셋 추가/삭제 |
| `SAFE` | 시계·위젯·하단버튼 위치 (화면 높이 대비 비율) |
| `L` | 문구 배치 비율 |
| `DEFAULTS` | 기본 문구 |
