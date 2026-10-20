# 1조 - 미니 게임 허브
팀장: 김민유 - https://github.com/rlaalsdb07/Creative-Engineering-Design

## 팀원 목록 및 GitHub 주소
- **김민유 (팀장,행맨)**: https://github.com/rlaalsdb07
- **김민재 (숫자야구)**: https://github.com/lJungDol
- **아델 마흐디에 (가위바위보)**: https://github.com/MHDIIH
- **전민성 (틱택토)**: https://github.com/min854014-beep

# 2조 - 미니 게임 허브
팀장: 한재원 — https://github.com/hanjaewon182/python_minigame_project_2team

## 팀장과 팀원 목록

| 역할 | 이름 | 담당 | GitHub 주소 |
|---|---|---|---|
| 팀장 (A, E) | 한재원 | 허브·저장소 관리, 틱택토 | https://github.com/hanjaewon182 |
| 팀원 (B) | 홍성민 | 행맨 | https://github.com/seongminhong497-cell |
| 팀원 (C) | 이민서 | 숫자 야구 | https://github.com/minseo9904 |
| 팀원 (D) | Manvika | 가위바위보 | https://github.com/themanvika |

## 특이사항

- 팀원이 4명이라 팀장(한재원)이 A(허브)와 E(틱택토) 역할을 함께 맡았습니다.
- 행맨 PR(#4) 리뷰는 팀장(한재원)이 진행했습니다.
- 가위바위보 후속 수정 PR(#6) 리뷰는 이민서가 진행했습니다.
- 가위바위보(PR #3)가 첫 번째로 병합되어 충돌이 발생하지 않았기 때문에, 후속 수정 PR(#6)을 올려 README 충돌을 해결하는 과정을 진행했습니다.

# 3조 - 미니 게임 허브
팀장: 황정호 - https://github.com/hwangjh0220/minigame_poject

## 팀장 및 팀원 목록

| 역할 | 이름 | GitHub 주소 |
|---|---|---|
| 팀장 | 황정호 | [https://github.com/hwangjh0220](https://github.com/hwangjh0220) |
| 팀원 | 고세진 | [https://github.com/kos070721-eng] |
| 팀원 | 양소제 | [https://github.com/yangsoje](https://github.com/yangsoje) |
| 팀원 | 싱프라쉬나 | [https://github.com/prashnaraa-byte] |

# 4조 A- 미니 게임 허브
팀장 : 정승현 - https://github.com/jungseunghyun0415/python_minigame_project

## 팀장과 팀원 목록

- 정승현 (팀장): https://github.com/jungseunghyun0415
- 박채민: https://github.com/huboisbingsin
- 김준우: https://github.com/wnsdn03651
- 로즈 와루구: https://github.com/rozie7

##  회고

-정승현:
      1. 가장 당황했던 순간은?

병합을 모두 끝낸 뒤 python main.py를 실행했는데 메뉴에 2번(숫자 야구)과 3번(가위바위보)만 나왔던 순간이다. PR은 전부 승인과 CI 통과를 거쳐 병합됐는데도 행맨과 틱택토가 메뉴에서 빠져 있었다.

원인을 찾아보니 충돌을 해결할 때 Accept both만 누르고 겹치는 줄과 주석 찌꺼기를 지우지 않은 것이었다. main.py에 baseball, rps import가 두 번씩 들어 있었고, GAMES 딕셔너리에는 들여쓰기가 어긋난 줄과 주석 줄이 남아 있었다. flake8로 확인하니 F811(중복 정의)과 E131(들여쓰기) 경고가 나왔다. 결국 fix/main-menu 브랜치를 따로 만들어 수정 PR을 올리고 팀원의 승인을 받아 다시 병합했다.

또 하나 당황스러웠던 것은 충돌을 해결한 뒤 내가 마지막으로 push한 PR을 내가 승인할 수 없고 Merge 버튼도 막힌 것이었다. 팀장이라고 예외가 아니라는 점이 처음에는 낯설었다.

2. 충돌은 왜 발생했고, 어떻게 줄일 수 있었을까?

왜 발생했나

모든 팀원이 같은 공용 파일의 같은 위치를 고쳤기 때문이다. main.py에서는 각자 자기 게임의 import 줄과 메뉴 줄 주석을 풀었고, README.md에서는 팀원 표의 같은 구간을 채웠다. 먼저 병합된 PR이 그 부분을 바꿔 놓으면 나머지 PR은 같은 줄을 서로 다르게 고친 셈이 되어 Git이 자동으로 합치지 못했다.

어떻게 줄일 수 있었나

공용 파일의 같은 줄을 여러 명이 고치지 않는 구조로 만든다. 예를 들어 main.py에 게임을 직접 적지 않고, games 폴더의 파일을 자동으로 찾아 등록하게 하면 각자 자기 파일만 만들어도 되어 충돌이 거의 사라진다.
README 팀원 표는 한 줄씩 떨어뜨리거나 팀원별 파일로 나눈다. 표의 연속된 줄을 동시에 고치면 충돌이 나기 쉽다.
병합 순서를 미리 공지하고, 병합될 때마다 각자 git merge main을 바로 해 둔다. 충돌을 한꺼번에 만나지 않고 작게 나눠서 풀 수 있다.
충돌 해결 후에는 반드시 flake8, pytest, python main.py를 확인하고 push한다. 이번에는 이 확인이 부족해서 중복 줄이 main까지 들어갔다.
3. 코드 리뷰에서 배운 점
리뷰는 코드를 눈으로 읽는 것보다 직접 받아서 실행해 보는 것이 먼저라는 것을 배웠다. git fetch, git switch로 틱택토를 받아 잘못된 입력과 승패 판정을 직접 넣어 보니, 읽기만 해서는 알 수 없는 것을 확인할 수 있었다.
pytest가 통과해도 테스트 개수가 적으면 충분하다고 볼 수 없다. 틱택토는 테스트가 2개뿐이어서 승리 판정과 무승부 테스트를 추가하면 좋겠다고 제안했다.
새 커밋이 올라오면 기존 승인이 무효화된다(Dismiss stale approvals)는 점을 직접 겪었다. 충돌을 해결하고 push할 때마다 재승인이 필요했고, 이 때문에 리뷰는 한 번으로 끝나지 않는다는 것을 알았다.
리뷰 댓글은 "~하세요"보다 "~하면 어떨까요?"로 쓰는 편이 받는 사람도 부담이 적고, 어느 줄이 왜 좋은지 적어야 상대에게 도움이 된다.
팀원이 4명이고 한 사람이 두 게임을 맡아서, 문서의 순환 리뷰표를 그대로 쓰면 자기 PR을 자기가 리뷰하게 되는 문제가 있었다. 그래서 자기 PR은 자기가 리뷰하지 않는 원칙으로 배정을 조정했다. 규칙은 팀 상황에 맞게 고쳐 써야 한다는 것을 배웠다.
4. 실무에서 팀에 제안하고 싶은 규칙 1가지

main 브랜치 보호 규칙에서 "Require status checks to pass before merging"을 켜서, CI(flake8 + pytest)가 통과하지 않은 PR은 병합하지 못하게 한다.

이번 실습에서는 이 옵션을 꺼 둔 상태였다. 충돌 해결 과정에서 중복 import 같은 형식 오류가 생겨도 승인만 있으면 병합이 가능했고, 병합한 뒤에야 메뉴가 깨진 것을 발견했다. CI 통과를 병합 조건으로 걸어 두면 사람이 실수해도 기계가 먼저 막아 주고, 리뷰어는 로직과 설계에 집중할 수 있다.

박채민:
충돌 해결하는 부분이 어려웠던것 같고 깃허브를 통해서 협업해보고 충돌을 해결하는 과정이 인상깊었습니다.

로즈 와루구루:
가장 당황했던 순간은 브랜치를 병합할 때 충돌이 발생했을 때였다. 처음에는 필요한 작업을 모두 완료했고 테스트도 통과했기 때문에 문제가 없을 것이라고 생각했다. 하지만 병합하려고 하자 충돌이 발생해서 무엇이 잘못되었는지 이해하기 어려웠다. 이 경험을 통해 테스트를 통과하는 것과 코드를 병합하는 것은 별개의 문제라는 것을 배웠다.

김준우:
팀원들과 코드를 리뷰하고 충돌 해결 하며 다시 리뷰하는 과정에서 합을 맞추는게 헷갈렸고 팀원들과 실무 협업 방식으로 과제를 하여 뜻깊었습니다.

# 5조 A- 미니 게임 허브
팀장: 이건영 - https://github.com/hwangjh0220/minigame_poject

## 팀장 및 팀원 목록
| 역할 | 이름 | GitHub ID | GitHub 주소 |
|---|---|---|---|
| A (팀장) | 이건영 | pachir1su | https://github.com/pachir1su |
| B | 김민건 | skyblue-d2f7ff | https://github.com/skyblue-d2f7ff |
| C | 조하민 | jhm829 | https://github.com/jhm829 |
| D | 류혁주 | edi0oa | https://github.com/edi0oa |

## 협업 흐름
main 최신화

  ↓
  
feature/<작업> 브랜치 생성

  ↓
  
개발 + 테스트

  ↓
  
작은 단위 commit

  ↓
  
push

  ↓
  
Pull Request

  ↓
  
다른 팀원 코드 리뷰

  ↓
  
Approve

  ↓
  
충돌 해결

  ↓
  
Merge

# 6조 - 미니 게임 허브
팀장: 박채환 - https://github.com/nyarq/python_minigame_project_team_06

<font color="red">Branches가 1개인데???</font>
## 팀장 및 팀원 목록
| 역할 | 이름 | GitHub 주소 |
|---|---|---|
| 팀장(A) | 박채환 (허브·저장소 관리) | https://github.com/nyarq |
| 팀원(B) | 이승재 (행맨) | https://github.com/foam0315 |
| 팀원© | 유수포프 사이드한 (숫자 야구) | https://github.com/Seidkhan-Yusupov |
| 팀원(D) | 변시우 (가위바위보) | https://github.com/byunsiwoo106-pixel |
| 팀원(E) | 김다현 (틱택토) | https://github.com/dreaminh07 |

# 7조 - 미니 게임 허브
팀장: 손세영 - https://github.com/seeyeongson/GameHub_skeleton.git

## 팀장 및 팀원 목록
| 이름 | GitHub 주소 |
|---|---|
| 손세영 | https://github.com/seeyeongson |
| 이주민 | https://github.com/villager168 |
| 한예성 | https://github.com/hanyeseong6-gif |
| 파젤리 샤디 | https://github.com/shadifazeli |
| 문지후 | 별도 연락 및 조 간 협업 없음 (사유 : 과제 제시일(10/06)부터 제출 마감일(10/18)까지 결석 및 연락 수단 없음) |

특이사항 - 문지후 팀원의 협업 불참에 따른 해당 과제물 미작업(틱택토) 은 팀장이 작업해서 올렸습니다.
