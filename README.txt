Thank you, Friends of Korea. 푸른눈의 독립운동가들에게 고마운 마음을 전해요. — 설치 순서 (AI 없는 버전)

필요한 것 : Supabase (이미 쓰는 "영어 아카이브" 프로젝트), 넷리파이. 깃허브와 Gemini 키는 필요 없습니다.

1. Supabase > SQL Editor > New query 에 setup.sql 내용을 붙여넣고 Run
   (표 4개 추가: ty_rooms, ty_cards, ty_reactions, ty_audio)
   ※ 이전 버전을 이미 설치했다면 setup.sql 맨 아래 alter 줄만 실행하세요 (becauseof, withoutyou, audio_public 칸 추가).
2. Project Settings > API 에서 Project URL 과 anon public key 복사 (service_role 키는 쓰지 마세요)
3. index.html 을 메모장으로 열어 맨 위 설정 3줄 수정
   const SUPABASE_URL = '...';
   const SUPABASE_KEY = '...';
   const TEACHER_PIN  = '...';   (교사 비밀번호, 꼭 변경)
4. 넷리파이 > Add new site > Deploy manually (또는 app.netlify.com/drop)
   index.html 이 들어 있는 폴더를 끌어다 놓으면 끝. 깃허브 연결은 필요 없습니다.
   (이미 올린 사이트라면 Deploys 에서 새 폴더를 끌어다 놓아 덮어쓰기)
5. 수업 : 반마다 다른 반 코드를 알려 주기 (예 : HAPPY51). 학생은 코드+번호만 입력.
   교사 : 오른쪽 위 "교사" > 반 코드 + 비밀번호 > "학생에게 벽 공개" 체크
   전자칠판에서 지도만 보여 주려면 주소 뒤에 ?map 을 붙입니다 (예 : https://내사이트.netlify.app/?map)

학생 화면 기능
- 문장 5칸 (Thank you for your ~ / You are ~ / Because of you, we can ~ / Without you, we could not ~ / I will ~) : 보기 낱말을 눌러서 넣거나 끌어다 놓기. 받는 사람에게 어울리는 말에는 ★. 백년길 문장(Because of…/Without…)은 하나 이상 필수
- 직접 쓰는 문장과 한국어 메모 칸은 없습니다. 칸 5개는 보기 낱말을 누르거나 📖 사전에서 찾아 씁니다.
- 카드 속 낱말을 누르면 한국어 뜻과 발음 소리 (내장 사전 약 170개, 없는 낱말은 사전 링크)
- 내 카드 듣기(🔊, 천천히/보통), 내 목소리 녹음(최대 40초, 필수), 벽에서 친구 카드 읽어 주기
- 벽 : 친구 카드에 ♥ 누르기 n/3, 한 마디는 선택
- 🗺 감사 지도 : 모든 반·학교의 카드가 한 장씩 쌓여 한반도 지도를 채웁니다 (카드가 적으면 편지가 크게, 많으면 작게). 카드 내용은 나오지 않고 위치만 나옵니다.
  다른 학교에서도 같은 사이트·같은 Supabase를 쓰면 함께 쌓입니다. 반 코드만 겹치지 않게 정하세요.
- 이름 등 개인정보는 받지 않습니다 (번호만).
- 녹음은 짧은 음성 파일(약 100~150KB)을 Supabase 표(ty_audio)에 저장합니다. 카드를 지우면 같이 지워집니다.
- 마이크는 https 주소에서만 작동합니다 (넷리파이는 https).

설정 3줄을 비워 두면 DEMO 모드(이 브라우저에만 저장)로 열립니다.

녹음 공개 : 녹음은 꼭 해야 올릴 수 있습니다. '친구들도 내 목소리를 들을 수 있게 할래요'는 쓴 학생이 선택(기본 꺼짐)하며, 선생님은 교사 모드에서 모든 학생의 녹음을 들을 수 있습니다.

보기 낱말 : 칸마다 10~12개이며, 학생 번호에 따라 보이는 순서가 달라 친구와 다른 카드를 만들기 쉽습니다. 받는 분에게 어울리는 말에는 ★.
교사 화면 : 카드를 인물별(전체 / Mr. Taylor / Dr. Schofield / Mr. Bethell / Mr. Hulbert) 탭으로 나눠 볼 수 있고, 탭마다 카드 수가 표시됩니다.
