가장 흔한 커밋 규칙(Conventional Commits 스타일)

fix: 버그/오류 수정

docs: 문서(README, 주석) 수정

style: 포맷/공백/세미콜론/정렬(동작 변화 없음)

refactor: 리팩토링(동작 변화 없음)

chore: 잡일(설정, 빌드, 패키지 등)

test: 테스트만 변경

예시(단순 수정에 딱 맞음)

docs: fix typo in README

style: format notebook cells

refactor: simplify input parsing

chore: update .gitignore

“WIP 커밋”은?

혼자 작업 중 임시 저장용이면

wip: … 로 쓰는 경우가 많지만,

가능하면 PR/공유 전에 rebase -i로 정리(스쿼시)하는 게 보통입니다.