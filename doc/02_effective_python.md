# Effective Python
* 브렛슬라킨의 59가지의 Better way
* https://github.com/gil

## 파이썬
### Betteer way 01. 사용 중인 파이썬의 버전을 알자
* 대중적인 런타임 환경 CPython, Jython, IronPython, PyPy
    ```bash
    $ python --version
    $ python3 --version
    ```
    ```python
    import sys
    print(sys.version_info)
    print(sys.version)
    ```

### Better way 02. PEP 8 스타일 가이드를 따르자
* Style Guide for Python Code  
    * https://www.python.org/dev/peps/pep-0008/
        * tab 대신 space 4개를 사용
        * 함수와 클래스는 빈 줄 두 개로 구분
        * 클래스에서 메서드는 빈 줄 하나로 구분
        * 함수, 변수, 속성은 lowercase_underscore
        * 보호(protected) 인스턴스 속성은 _leading_underscore 형식
        * 비공개(private) 인스턴스 속성은 __double_leading_underscore 형식
        * 클래스와 예외는 CapitalizedWord 형식
        * 모듈 수준 상수는 ALL_CAPS 형식
        * 클래스의 인스턴스 메소드 첫 번째 파라미터는 'self'
        * 클래스의 메서드 첫 번째 파라미터는 'cls'
        * 긍정 표현식의 부정(if not a is b) 보다 인라인 부정(if a is not b)을 사용
        * 빈 값을 확인은 (if len(somelist) == 0) 말고 if not somelist를 사용
        * 값의 존재 확인은 if someList 사용
        * 파일의 맨 앞에 import문 위치
            * 상대적 import가 아닌 절대적 import 사용
                * import foo 이 아닌 from bar import foo
                * 상대적 import 사용시에는 from . import foo
            * 표준 라이브러리의 모듈, 서드파티 모듈, 자신이 만든 모듈순
            * 각각 알파벳순
    * Pylint 도구 http://www.pylint.org        
        * 자동으로 PEP8 스타일 가이드를 강요하고 오류를 검출
        
### Better way 03. bytes, str, unicode의 차이점을 알자
### Better way 04. 복잡한 표현식 대신 헬퍼 함수를 사용하자
### Better way 05. 시퀀스를 슬라이스하는 방법을 알자
### Better way 06. 한 슬라이스에 start, end, stride를 함께 쓰지 말자
### Better way 07. map과 filter 대신에 리스트 컴프리헨션을 사용하자
### Better way 08. 리스트 컴프리헨션에서 표현식을 두 개 넘게 쓰지 말자
### Better way 09. 컴프리헨션이 클 때는 제너레이터 표현식을 고려하자
### Better way 10. range보다는 enumerate를 사용하자
### Better way 11. 이터레이터를 병렬로 처리하려면 zip을 사용하자
### Better way 12. for와 while 루프 뒤에는 else 블록을 쓰지 말자
### Better way 13. try/except/ese/finally에서 각 블록의 장점을 이용하자

## 2장. 함수
### Better way 14. None을 반환하기 보다 예외를 일으키자
### Better way 15. 클로저가 변수 스코프와 상호 작용하는 방법을 알자
### Better way 16. 리스트를 반환하는 대신 제너레이터를 고려하자
### Better way 17. 인수를 순회할 때는 방어적으로 하자
### Better way 18. 가변 위치 인수로 깔끔하게 보이게 하자
### Better way 19. 키워드 인수로 선택적인 동작을 제공하자
### Better way 20. 동적 기본 인수를 지정하려면 None과 docstring을 사용하자
### Better way 21. 키워드 전용 인수로 명료성을 강요하자

## 3장. 클래스와 상속
### Better way 22. 딕셔너리와 튜플보다는 헬퍼 클래스로 관리하자
### Better way 23. 인터페이스가 간단하면 클래스 대신 함수로 받자
### Better way 24. 객체를 범용으로 생성하려면 @classmethod 다형성을 이용하자
### Better way 25. super로 부모 클래스를 초기화하자
### Better way 26. 믹스인 유틸리티 클래스에만 다중 상속을 사용하자
### Better way 27. 공개 속성보다는 비공개 속성을 사용하자
### Better way 28. 커스텀 컨테이너 타입은 collection.abc의 클래스를 상속받게 만들자.

## 4장. 메타클래스와 속성
### Better way 29.  게터와 세터 메서드 대신에 일반 속성을 사용하자
### Better way 30.  속성을 리팩토링하는 대신 @property를 고려하자
### Better way 31.  재사용 가능한 @property 메서드에는 디스크럽터를 사용하자
### Better way 32.  지연 속성에는 \__getattr__, \__getattribute__, \__setattr__을 사용하자
### Better way 33.  메타클래스로 서브클래스를 검증하자
### Better way 34.  메타클래스로 클래스의 존재를 등록하자
### Better way 35.  메타클래스로 클래스 속성에 주석을 달자

## 5장. 병행성과 병렬성
### Better way 36.  자식 프로세스를 관리하려면 subprocess를 사용하자
### Better way 37.  스레드를 블로킹 I/O용으로 사용하고 병렬화용으로는 사용하지 말자
### Better way 38.  스레드에서 데이터 경쟁을 막으려면 Lock을 사용하자
### Better way 39.  스레드 간의 작업을 조율하려면 Queue를 사용하자
### Better way 40.  많은 함수를 동시에 실행하려면 코루틴을 고려하자
### Better way 41.  많은 함수를 동시에 실행하려면 코루틴을 고려하자

## 6장. 내장 모듈
### Better way 42.  functions.wrap로 함수 데코레이터를 정의하자
### Better way 43.  재사용 가능한 try/finally 동작을 만들려면 contextlib와 with문을 고려하자
### Better way 44.  copyreg로 pickle을 신뢰할 수 있게 만들자
### Better way 45.  지역 시간은 time이 아닌 datetime으로 표현하자
### Better way 46.  내장 알고리즘과 자료 구조를 사용하자
### Better way 47.  정밀도가 중요할 때는 decimal을 사용하자
### Better way 48.  커뮤니티에서 만든 모듈을 어디서 찾아야 하는지 알아두자


## 7장. 내장 모듈
### Better way 49.  모든 함수, 클래스, 모듈에 docstring을 작성하자
### Better way 50.  모듈을 구성하고 안정적인 API를 제공하려면 패키지를 사용하자
### Better way 51.  루트 Exception을 정의해서 API로부터 호출자를 보호하자
### Better way 52.  순환 의존성을 없애는 방법을 알자
### Better way 53.  의존성을 분리하고 재현하려면 가상 환경을 사용하자

## 8장. 제품화
### Better way 54.  배포 환경을 구성하는 데는 모듈 스코프 코드를 고려하자
### Better way 55.  디버깅 출력용으로는 repr 문자열을 사용하자
### Better way 56.  unittest로 모든 것을 테스트하자
### Better way 57.  pdb를 이용한 대화식 디버깅을 고려하자
### Better way 58.  최적화하기 전에 프로파일하자
### Better way 59.  tracemalloc으로 메모리 사용 현황과 누수를 파악하자
