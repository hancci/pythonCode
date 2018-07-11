# python syntax
* 함수 + 모듈 = 표준 라이브러리
    ```python
    from datetime import datetime

    odds = [1,3,5,7,9,11,13,15,17,19,21,23,25,27,29,31
                ,33,35,37,39,41,43,45,47,49,51,53,55,57,59]

    right_this_minute = datetime.today().minute


    if right_this_minute in odds :
        print("odd")
    else :
        print("even")
    ```
* getcwd는 함수, os 표준 라이브러리
    ```python
    from os import getcwd
    ```

* 표준 라이브러리
    * https://docs.python.org/3/library/index.html

* 서드파티 모듈
    * https://pypi.python.org/pypi
    
* 현재 파이썬을 실행하는 플랫폼이 dawin이고 이는 맥 os x의 커널명임을 보여줌
    ```python
    >>> import sys
    >>> sys.platform
    'darwin'
    ```
* import 예제
    ```python
    # time모듈을 임포트하라는 명령
    import time
    time.sleep(5)
        """
        모듈A,B에 동일한 이름의 function F가 있다면
        from A import F
        from B import F
        로 하면 사용할 수가 없으니
        import A
        import B
        로 하고 A.F(), B.F()로 호출
        """

    # 네임스페이스로 함수 이름을 임포트
    from datetime import datetime
    datetime.today().minute

    # 모듈에 대한 모든 속성을 표시
    import random
    dir(random)

    # 사용법 확인 가능
    help(dir)
    help(random.randint)
    ```
    * 모듈을 찾는 3가지 방법
        * 동일디렉토리
        * 사이트 패키지
        * 표준 라이브러리

* datetime 예제
    ```python
    >>> import datetime
    >>>
    >>> datetime.date.today()
    datetime.date(2018, 7, 10)
    >>>
    >>> datetime.date.today().year
    2018
    >>> datetime.date.today().day
    10
    >>> datetime.date.today().month
    7
    >>> datetime.date.isoformat(datetime.date.today())
    '2018-07-10'
    ```

* time 예제
    ```python
    >>> import time
    >>> time.strftime("%H:%M")
    '14:17'
    >>>
    >>> time.strftime("%A %p")
    'Tuesday PM'
    >>> time.sleep(5)
    ```

* html 예제
    ```python
    >>> import html
    >>> html.escape("<html></html>")
    '&lt;html&gt;&lt;/html&gt;'

    >>> html.unescape('&lt;html&gt;&lt;/html&gt;')
    '<html></html>'
    >>>
    ```
* 스위트(suite)
    * 파이썬은 코드 블록이란 말 대신 스위트suite라는 표현을 사용
    * 들여쓰기로 코드블록을 표시
    ```python
    if today== 's':
        print('s')
    elif today == 'sun':
        print('sun')
    else:
        print('else')
    ```
* 데이터 타입
    * 파이썬에서는 모든 것이 객체 (숫자, 문자열, 함수, 모듈등)
    * object oriented 보다 object based라는 표현이 더 적절
* 변수
    * 파이썬 변수는 동적으로 할당됨
    * 미리 선언할 필요없음

* 자료구조
    * 내장 기능으로 제공하는 자료구조
    * 언어의 일부라서 import가 필요없음
        * list: [] , list()
            * 순서가 있고, mutable(변경할수 있는) 객체 컬렉션
            * 동적 크기 변경. 미리 사이즈 지정 불필요
            * 선언 불필요 
            * 여러 종류의 객체 저장 가능
            * 배열과 비슷
        * tuple: (), tuple()
            * 순서가 있고, immutable(변경할 수 없는) 객체 컬렉션
            * 상수 리스트와 같음
        * dictionary {}, dict()
            * 순서가 없는 key - value
            * 다른 언어에서는 연관배열, 맵, 심벌 테이블, 해시등의 이름으로 사용
            * c++, java에서는 Map
            * perl, ruby에서는 hash
            * python에서는 dictionary 줄여서 딕
        * set : set()
            * 순서가 없는 중복없는 집합

* for
    * Sequence Type
        ```python
        for i in [1,2,3]:
            print(i)

        for num in range(5):
        	print('head first')

        ```    

* list
    * https://docs.python.org/3/library/stdtypes.html#mutable-sequence-types
    ```python
    vowels = ['a', 'e', 'i', 'o', 'u']
    word = input("Provide a word to search for vowels: ")
    found = []
    for letter in word:
        if letter in vowels:
            if letter not in found:
                found.append(letter)
    for vowel in found:
        print(vowel)

    # append('값')
    # remove('값')
    # pop() : 마지막 값 리턴하고 list에서 제거
    # pop(index) : 0부터
    # extend([3,4]) : 리스트 뒤에 동적으로 추가
    # insert(index, 값) : index앞에 값 추가

    help(list) 
    type(list)
    ```
* dict
    * https://docs.python.org/3/library/stdtypes.html#mapping-types-dict
    ```python
    >>> d = {"one": 1, "two": 2, "three": 3, "four": 4}
    >>> d
    {'one': 1, 'two': 2, 'three': 3, 'four': 4}

    >>> list(d)
    ['one', 'two', 'three', 'four']

    >>> list(d.values())
    [1, 2, 3, 4]

    >>> d["one"] = 42
    >>> d
    {'one': 42, 'two': 2, 'three': 3, 'four': 4}

    >>> del d["two"]
    >>> d["two"] = None
    >>> d
    {'one': 42, 'three': 3, 'four': 4, 'two': None}

    ```
    ```python
    vowels = ['a', 'e', 'i', 'o', 'u']
    word = input("Provide a word to search for vowels: ")

    found = {}
    for letter in word:
        if letter in vowels:
            found.setdefault(letter, 0)
            found[letter] += 1

    for vowel in sorted(found):
        print(vowel, 'occurred', found[vowel], 'times.')

    print('----')

    for vowel in sorted(found, key=found.get, reverse=True):
        print(vowel, 'occurred', found[vowel], 'times.')

    print('----')

    for k, v in sorted(found.items()):
        print(k, 'was found', v, 'time(s).')

    e occurred 1 times.
    i occurred 3 times.
    o occurred 2 times.
    ----
    i occurred 3 times.
    o occurred 2 times.
    e occurred 1 times.
    ----
    e was found 1 time(s).
    i was found 3 time(s).
    o was found 2 time(s).

    ```
* slice
    ```python
	plist[1:3]
	booklist[::-1]
	booklist[::2]
	booklist[4:14]
	booklist[13:3:-1]
    ```

* Boolean 예제
    ```python
    bool(0)
    bool(0.0)
    bool('')
    bool([])
    bool({})
    bool(None)
    ==> False

    bool(1)
    bool(-1)
    bool(42)
    bool(0.000001)
    bool('Panic')
    bool([43,44,45])
    bool({'a':42, 'b':44})
    ==> True
    ```
* open 예제
    ```python
    tasks = open('todos.txt')
    for chore in tasks:
	    print(chore)
    tasks.close()
    ```
    * with문은 컨텍스트 관리 프로토콜이라는 내장 파이썬 코딩 규칙을 준수
    * with문은 close가 필요없음
    ```python
    with open('todos.txt') as tasks:
	    for chore in tasks:
		    print(chore)
    ```
    ```python
    # read는 모든 문자를 한번에 읽음.
    import os
    os.chdir('/Users/Paul/buzzdata')
    with open('buzzers.csv') as raw_data:
        print(raw_data.read())
    ```

    ```python
    # 각행을 리스트로 반환함. line은 list임. 헤더정보를 무시함.
    import csv
    with open('buzzers.csv) as data:
        for line in csv.read(data):
            print(line)
    ```

    ```python
    # 각행을 딕셔너리로 반환함   
    import csv
    with open('buzzers.csv) as data:
        for line in csv.DicReader(data):
            print(line)
    
    ```

* 객체 예제
    ```python
    # __init__ 객체 초기화
    # __repr__ 객체를 어떻게 표현할지 결정

    class CountFromBy:

        def __init__(self, v: int=0, i: int=1) -> None:
            self.val = v
            self.incr = i

        def increase(self) -> None:
            self.val += self.incr

        def __repr__(self) -> str:
            return str(self.val)


    h = CountFromBy(100,10)
    h.increase()
    h.increase()
    print(h)
    h.increase()
    print(h)
    ```

    * @staticmethod 
        * 클래스안에서 정적함수를 만들수 있도록 해주는 장식자
	    * self를 첫번째인자로 받지 않음.

    * @classmethod 
	    * 클래스 메소드에서 첫번째 객체를 selft가 cls라는 클래스로 받을 수 있는 기능을 제공하는 장식자

    * @property
	    * 메서드를 마치 속성처럼 이용할 수 있도록 재설계해주는 장식자

    * __slots 
        * 클래스로 만든 객체의 메모리 효율성을 크게 개선할 수 있는 클래스 지시어. 
        * 대신 약간의 융통성이라는 비용을 지불해야함


문자열 formatspec
docs.python.org/3/library/string.html#formatspec


* 컨텍스트 관리 프로토콜
    * 컨텍스트 관리자를 만든다는 것은 컨텍스트 관리 프로토콜을 준수하는 새 클래스를 만들어 with문과 연결하는 것을 말함
    * 아래 두 메소드를 반드시 정의
        * `__enter__` : 설정을 담당함. with문 스위트를 시작하면 호출함.
        * `__exit__` : 마무리를 담당
    * enter와 exit가 있는 모든 클래스는 컨텍스트 관리자임. with문과 연결가능.
    * __init__이 있다면 먼저 __init__이 호출됨. with문 시작전에 호출됨.
    ```python
    with open('todos.txt') as task
        for chore in tasks:
            print(chore, end=' ')
    ```
    ```python
    import mysql.connector


    class UseDatabase:
        def __init__(self, config: dict):
            """Add the database configuration parameters to the object.

            This class expects a single dictionary argument which needs to assign
            the appropriate values to (at least) the following keys:

                host - the IP address of the host running MySQL/MariaDB.
                user - the MySQL/MariaDB username to use.
                password - the user's password.
                database - the name of the database to use.

            For more options, refer to the mysql-connector-python documentation.
            """
            self.configuration = config

        def __enter__(self) -> 'cursor':
            """Connect to database and create a DB cursor.

            Return the database cursor to the context manager.
            """
            self.conn = mysql.connector.connect(**self.configuration)
            self.cursor = self.conn.cursor()
            return self.cursor

        def __exit__(self, exc_type, exc_value, exc_traceback):
            """Destroy the cursor as well as the connection (after committing).
            """
            self.conn.commit()
            self.cursor.close()
            self.conn.close()


    def log_request(req: 'flask_request', res: str) -> None:
        """Log details of the web request and the results."""

        with UseDatabase(app.config['dbconfig']) as cursor:
            _SQL = """insert into log
                    (phrase, letters, ip, browser_string, results)
                    values
                    (%s, %s, %s, %s, %s)"""
            cursor.execute(_SQL, (req.form['phrase'],
                                req.form['letters'],
                                req.remote_addr,
                                req.user_agent.browser,
                                res, ))

    ```

* 함수 장식자
    * *args : 리스트값을 확장하는 의미의 튜플
    ```python
    def myfunc(*args):
        for a in args:
            print(a, end=' ')
        if args:
            print()

    >>> values = [1,2,3,4,5]

    >>> myfunc(values)
    [1, 2, 3, 4, 5]

    >>> myfunc(*values)
    1 2 3 4 5
    # 리스트앞에 *를 붙이면 리스트를 확장하도록 인터프리터에게 명령.
    # 마치 여러개의 인자를 전달받는 것과 같음
    ```
    * **kwargs 딕셔너리를 확장하는 의미
    ```python
    def myfunc2(**kwargs):
        for k, v in kwargs.items():
            print(k, v, sep='->', end=' ')
        if kwargs:
            print()


    >>> myfunc2(a=10, b=20)
    a->10 b->20
    ```
    * 장식자 만들기
        * 함수 장식자는 함수임
        * 장식자는 장식된 함수를 인자로 받음
        * 장식자는 새 함수를 반환함
        * 장식자는 장식된 함수의 시그너치를 유지함
    ```python
    from functools import wraps

    def check_logged_in(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            if 'logged_in' in session:
                return func(*args, **kwargs)
            return 'You are NOT logged in.'
        return wrapper


    @app.route('/page1')
    @check_logged_in
    def page1():
        return 'This is page 1.'
    ```
* 예외처리
    ```python

    try:
        with open('myfile.txt') as fh:
            file_data = fh.read()
        print(file_data)
    except FileNotFoundError:
        print('The data file is missing.')
    except PermissionError:
        print('This is not allowed.')
    except Exception as err:
        print('Some other error occurred:', str(err))

    >>> import sys
    >>> try:
    ...     1/0
    ... except:
    ...     err=sys.exc_info()
    ...     for e in err:
    ...             print(e)
    ...
    <class 'ZeroDivisionError'>
    division by zero
    <traceback object at 0x00000247AA44F788>

    >>> class ConnectionError(Exception):
    ...     pass
    ...
    >>> raise ConnectionError('Cannot connect... is it time to panic ?')
    Traceback (most recent call last):
    File "<stdin>", line 1, in <module>
    __main__.ConnectionError: Cannot connect... is it time to panic ?
    >>>

    >>> try:
    ...     raise ConnectionError('Whoops')
    ... except ConnectionError as err:
    ...     print('Got', str(err))
    ...
    Got Whoops
    ```
* 쓰레드
    ```python
    from threading import Thread


    def log_request(req: 'flask_request', res: str) -> None:
        """Log details of the web request and the results."""

        # raise Exception("Something awful just happened.")
        
        sleep(15)  # This makes log_request really slow...

        with UseDatabase(app.config['dbconfig']) as cursor:
            _SQL = """insert into log
                    (phrase, letters, ip, browser_string, results)
                    values
                    (%s, %s, %s, %s, %s)"""
            cursor.execute(_SQL, (req.form['phrase'],
                                req.form['letters'],
                                req.remote_addr,
                                req.user_agent.browser,
                                res, ))

    @app.route('/search4', methods=['POST'])
    def do_search() -> 'html':
        """Extract the posted data; perform the search; return results."""
        phrase = request.form['phrase']
        letters = request.form['letters']
        title = 'Here are your results:'
        results = str(search4letters(phrase, letters))
        try:
            t = Thread(target=log_request, args=(request, results))
            t.start()
        except Exception as err:
            print('***** Logging failed with this error:', str(err))
        return render_template('results.html',
                            the_title=title,
                            the_phrase=phrase,
                            the_letters=letters,
                            the_results=results,)
    ```
* 고급 반복 Comprehension
    * list comprehension을 줄여서 listcomp
    * dictcomp
    * setcomp가 있음
    * 튜플 컴프레헨션은 없음
    ```python
    data=[1,2,3,4,5,6,7,8,]
    evens = []
    for num in data:
    if not num % 2:
        evens.append(num)

    # 
    evens = [even for even in [1,2,3,4,5,6,7,8,] if even % 2 == 0]
    ```

    ```python
    data = [1, 'one', 2, 'two', 3, 'three', 4, 'four']
    words = []
    for num in data:
        if isinstance(num, str):
            words.append(num)

    print(words)

    ['one', 'two', 'three', 'four']

    대신
    words = [num for num in data if isinstance(num, str)]
    print(words)

    ['one', 'two', 'three', 'four']

    ```

    ```python
     from datetime import datetime
    from pprint import pprint


    def convert2ampm(time24: str)->str:
        return datetime.strptime(time24, '%H:%M').strftime('%I:%M%p')


    with open('./buzzers.csv') as data:
        ignore = data.readline()
        flights = {}
        for line in data:
            k, v = line.strip().split(',')
            flights[k] = v

    pprint(flights)
    print()

    fts = {convert2ampm(k): v.title() for k, v in flights.items()}

    pprint(fts)
    print()

    when = {dest: [k for k, v in fts.items() if v == dest] for dest in set(fts.values())}

    pprint(when)
    print()

    {'09:35': 'FREEPORT',
    '09:55': 'WEST END',
    '10:45': 'TREASURE CAY',
    '11:45': 'ROCK SOUND',
    '12:00': 'TREASURE CAY',
    '17:00': 'FREEPORT',
    '17:55': 'ROCK SOUND',
    '19:00': 'WEST END'}

    {'05:00PM': 'Freeport',
    '05:55PM': 'Rock Sound',
    '07:00PM': 'West End',
    '09:35AM': 'Freeport',
    '09:55AM': 'West End',
    '10:45AM': 'Treasure Cay',
    '11:45AM': 'Rock Sound',
    '12:00PM': 'Treasure Cay'}

    {'Freeport': ['09:35AM', '05:00PM'],
    'Rock Sound': ['11:45AM', '05:55PM'],
    'Treasure Cay': ['10:45AM', '12:00PM'],
    'West End': ['09:55AM', '07:00PM']}

    ```
    ```python
    when = {dest: [k for k, v in fts.items() if v == dest] for dest in set(fts.values())}

    ## 아래 문장과 동일함
    when = {}
    for dest in set(fts.values()):
        when[dest] = [k for k, v in fts.items() if v == dest]
    ```

    ```python
    # 튜플은 생성기일 때 comprehension을 사용할 수 있음

    for i in (x*3 for x in [1,2,3,4,5]):
        print(i)

    for i in [x*3 for x in [1,2,3,4,5]]:
        print(i)
    ```

    * 리스트컴프는 데이터가 다 만들어지기 전까지는 loop 수행안함.
    * 생성기는 만들어지면서 loop 수행함.=> 성능적인 이점.
    ```python
    import requests

    urls = ('http://headfirstlabs.com', 'http://oreilly.com', 'http://twitter.com')

    for resp in [requests.get(url) for url in urls]:
        print(len(resp.content), '->', resp.status_code, '->', resp.url)

    # 성능비교

    import requests

    urls = ('http://headfirstlabs.com', 'http://oreilly.com', 'http://twitter.com')

    for resp in (requests.get(url) for url in urls):
        print(len(resp.content), '->', resp.status_code, '->', resp.url)
    ```

* yield 예제
    * yield 는 생성기 함수를 만들수 있도록 추가된 함수
    ```python
    import requests

    def gen_from_urls(urls: tuple) -> tuple:
        for resp in (requests.get(url) for url in urls):
            yield len(resp.content), resp.status_code, resp.url


    urls = ('http://headfirstlabs.com', 'http://oreilly.com', 'http://twitter.com')

    for resp_len, status, url in gen_from_urls(urls):
        print(resp_len, status, url)

    ```

* 문자열
    * https://docs.python.org/3/library/string.html#formatspec

* library
    * https://docs.python.org/3/library/index.html

    * collections
        * OrderedDict 삽입순서를 유지
        * Counter 쉽게 셀 수 있는 기능
        * ChainMap 한개이상의 딕을 합쳐 한개로 나타냄

    * itertool : 커스텀 반복을 만드는 유용한 컬렉션 도구를 제공
        * product
        * permutations
        * combinations

    * functools
        * 객체함수를 인자로 갖는 함수인 고차원 함수 컬렉션을 제공

    * 병렬처리
        * threading 모듈외
        * multiprocessing 여러 프로세스사용
        * asyncio 
        * concurrent.futures 태스크 컬렉션을 관리하고 동시 실행

    * async, await
        * for, with, def 앞에 쓸수 있음 하지만 조심해야함.

    * GIL : Global Interpreter Lock
        * 인터프리터가 안정성을 유지하는 수단으로 사용하는 내부 기법.
        * 파이썬 커뮤니티에서 자주 토론과 논쟁

    * Tkinter 를 이용한 GUI, 그리고 Turtle 의 묘미

    * doctest 모듈의 docstring에 테스트를 추가할 수 있음
    * unitest 파이썬 자체 유닛테스트버전을 제공=> 별로
    * 디버그:
	    * python3 -m pdb myprog.py

    * pdb 운영체제의 터미널창으로 디버깅하는 방법
        * docs.python.org/3/library/pdb.html
