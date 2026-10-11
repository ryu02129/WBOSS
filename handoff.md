# Handoff

## 게시물

- https://www.instagram.com/p/DeHAbMjj705/
- 게시자 @ai.trend.kr (2026-10-05), 원작자 @dding_one
- 슬라이드 7장짜리 게시물 (영상 6개, 이미지 1장)

## 이전 세션에서 본 내용 (참고용)

이전 작업 환경(클라우드)에서 캡션을 읽고, 영상을 1초 간격으로 캡처해서 본 내용이다.

- 캡션: 결혼식 방명록을 펜 대신 셀카로 쓴다. 하객이 사진을 올리면 닮은 픽셀 캐릭터가 생기고, 축하 메시지를 남기면 결혼식장 꽃길로 입장한다. 2026-08-29 실제 결혼식에서 썼고, 식장 스크린에 띄웠다. 바이브코딩으로 만들었고, 11~12월 정식 출시 예정이라고 한다.
- 하객 휴대폰 화면 (어두운 테마)
  - 셀카를 올리면 "픽셀 옷 입는 중…" 로딩이 뜨고 캐릭터 후보 4개가 생성된다.
  - "마음에 드는 캐릭터를 선택해 주세요" 화면에서 하나를 고른다.
  - "캐릭터 이름과 말풍선 대사를 입력해 주세요" 화면에서 이름과 대사를 입력한다.
- 꽃길 화면
  - 위에서 내려다보는 RPG 스타일의 숲속 야외 식장이다. 꽃 아치 아래에 신랑·신부가 이름표를 달고 서 있다.
  - 하객 캐릭터들은 이름표를 달고 꽃길과 잔디를 돌아다닌다. 축하 말풍선이 한 글자씩 써지는 효과로 떠오른다.
  - 신랑·신부도 말풍선을 띄운다. 그중 "저를 누르면 사진을 볼 수 있어요!"는 누르면 사진이 열린다.
  - 하객이 수백 명까지 늘어난 상태도 나온다.
- 식장 대형 스크린
  - 왼쪽에 꽃길 화면과 접속용 QR 코드, 오른쪽에 최근 메시지 목록(캐릭터 얼굴, 이름, 대사)이 있다.
  - 별도 연출이 있다.
    - "3rd CHAPTER 우리가 함께한 날들": 횡스크롤 장면 위로 실제 커플 사진이 나온다.
    - 픽셀 실내 예식장 장면과 "○○ ♥ ○○ 결혼식 지금부터 시작합니다" 자막이 나온다.
    - 원형으로 좁혀지며 닫히는 화면 전환이 있다.

## 사용자가 말한 것

- 범위: 하객 화면, 꽃길 화면, 대형 스크린(QR과 메시지 목록)을 먼저 만든다. 챕터 연출은 나중에 한다.
- 비용: 돈은 한 푼도 쓰지 않는다. 유료 API와 호스팅 서비스는 쓰지 않는다.
- 이미지 생성: 오픈소스 모델을 로컬 GPU에서 돌린다.
- 작업 장소: 클라우드에는 GPU가 없어서 로컬에서 작업한다.
- 브랜치: 이름만 봐도 알 수 있게 `feature/pixel-wedding-guestbook`을 쓴다.
- 이 저장소(WBOSS)에는 이 파일 말고 README만 있다.

## 이전 세션에서 찾아본 오픈소스 (검증 안 됨)

GPU가 없는 환경이라 아래 모델과 도구는 하나도 실행해보지 못했다.

- 사진을 픽셀 캐릭터로 바꾸는 모델
  - Qwen-Image-Edit-2511 (Apache 2.0) + [Render It LoRA](https://huggingface.co/AmirKerr/Render_It) (pixelart 스타일이 있음)
  - FLUX.2-klein-4B + [Limbicnation/pixel-art-lora](https://huggingface.co/Limbicnation/pixel-art-lora) (투명 배경 512px 캐릭터 스프라이트)
  - 그 외: [pixel-art-xl](https://huggingface.co/nerijs/pixel-art-xl), [pixel-party-xl](https://huggingface.co/pixelparty/pixel-party-xl) (둘 다 SDXL 기반)
- AI 결과물을 실제 픽셀 격자와 적은 색 수로 정리하는 도구: [unfake](https://pypi.org/project/unfake/) (JS판·Python판), [proper-pixel-art](https://github.com/KennethJAllen/proper-pixel-art)
- 정지 캐릭터에 걷는 애니메이션을 입히는 모델: [Wan2-2-pixel-animate](https://huggingface.co/styly-agents/Wan2-2-pixel-animate)
- 사용자의 GPU 모델명과 VRAM 용량은 아직 모른다.
