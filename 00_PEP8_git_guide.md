## font
리눅스 사용 폰트
- DejaVu Sans Mono -> Editor: Font Family, notebook
- AppleSDGothicNeoR00 -> markdown font


## git guide
가장 흔한 커밋 규칙(Conventional Commits 스타일)

- fix: 버그/오류 수정
- docs: 문서(README, 주석) 수정
- style: 포맷/공백/세미콜론/정렬(동작 변화 없음)
- refactor: 리팩토링(동작 변화 없음)
- chore: 잡일(설정, 빌드, 패키지 등)
- test: 테스트만 변경

예시(단순 수정에 딱 맞음)
- docs: fix typo in README
- style: format notebook cells
- refactor: simplify input parsing
- chore: update .gitignore

“WIP 커밋”은?
혼자 작업 중 임시 저장용이면 wip: … 로 쓰는 경우가 많지만,
가능하면 PR/공유 전에 rebase -i로 정리(스쿼시)하는 게 보통입니다.`

## PEP8_Python Enhancement Proposal 8

### 기본가이드
- PEP 8은 4칸 공백으로 들여쓰기(탭은 사용 금지)
- 한 줄을 79자로 제한
- 변수는 my_variable (스네이크 케이스)
- 클래스는 MyClass (카멜 케이스)
    ```Python
    # Bad (나쁜 예)
    myVar = 10
    class my_class:
        pass

    # Good (좋은 예)
    my_variable = 10
    class MyClass:
        pass
    ```

### 띄어쓰기
- 파라미터 값을 나타낼 때는 '='주변에 띄어쓰기를 하지않음
- 반대로 “대입문”에서는 공백을 넣는 게 기본
    ```Python
    # 함수 정의 (default)
    def foo(x=1, y=None):
        ...

    # 함수 호출 (keyword argument)
    foo(x=1, y=2)

    # 대입문에서는 공백이 기본
    x = 1
    total = a + b
    ```

### 타입 힌트 (Type Hints): 코드의 명확성
- C와 다르게 변수가 어떤 타입인지 몰라서 혼동이 올수 있음
- 파이썬 3.5부터 도입된 이 기능은 코드의 가독성을 크게 향상
- 6개월 뒤 나를 위한 행동
    ```python
    # Without type hinting (타입 힌트 없이)
    def add(a, b):
        return a + b

    # With type hinting (타입 힌트 사용)
    def add(a: int, b: int) -> int:
        return a + b
    ```


### with 문: 파일 처리 및 리소스 관리를 안전하게
- 이전 방식으로 파일을 열면 특히 오류가 발생할 경우 파일을 닫는 것을 잊어버릴 위험 있음.
- with 문은 이 작업을 자동으로 파일 닫아서 처리
    ```python
    # Without context manager (컨텍스트 관리자 없이)
    file = open("data.txt", "r")
    text = file.read()
    file.close()  # 이 줄 이전에 에러가 발생하면 위험!

    # With context manager (컨텍스트 관리자 사용)
    with open("data.txt", "r") as file:
        text = file.read()  # 완료되면 자동으로 닫힘
    ```


### 데이터클래스 (Dataclasses): 데이터 저장용 클래스를 간결하게 정의
- 데이터클래스는 반복적인 작업을 줄여줍니다.
    ```Python
    # Without dataclass (데이터클래스 없이)
    class Person:
        def __init__(self, name, age):
            self.name = name
            self.age = age

    # With dataclass (데이터클래스 사용)
    from dataclasses import dataclass

    @dataclass
    class Person:
        name: str
        age: int

    p = Person("Alice", 30)  # 동일하게 작동합니다!
    ```

### 예외 처리 (Exception Handling): 프로그램 충돌을 방지하고 안정성을 확보하세요.
- 언제나 오류는 발생
- 위험한 코드를 try/except 블록으로 감싸서 계속 실행되도록
    ```Python
    # Bad: No error handling (나쁜 예: 오류 처리 없음)
    result = 10 / 0

    # Good (좋은 예)
    try:
        result = 10 / 0
    except ZeroDivisionError:
        print("Cannot divide by zero!")
    ```

### 유닛 테스트 (Unit Tests): 코드의 품질과 안정성을 확보하세요.
- 테스트를 작성하는 것은 추가 작업처럼 느껴지지만, 버그가 프로덕션에 배포되기 전에 잡는다면 가치가 있음
    ```Python
    import unittest

    def add(a, b):
        return a + b

    class TestMath(unittest.TestCase):
        def test_add(self):
            self.assertEqual(add(2, 3), 5)

    if __name__ == "__main__":
        unittest.main()
    ```







