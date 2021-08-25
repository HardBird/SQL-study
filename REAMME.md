SQL 정리노트 
=============

# SELECT ~ FROM ~ WHERE
##### SELECT DISTINCT : 중복배제 
##### SELECT * : 전체출력 
-기본적인 구조는 공백으로 구분하여 사용한다 
-괄호는 ()로만 해결할 수 있다.
-MIN,MAX,ABS,COUNT,AVG,SUM을 사용할 수 있다. (NULL값은 포함이 되지 않음)
* * *
##### CONCAT : 여러 문자열 합치기 
> ###### CONCAT 예제 
> - SELECT CONCAT(region_name,' ',store_name) FROM Georaphy WHERE strore_name = 'Boston'; 
> Geography 테이블에서 store_name이 Boston인 데이터인 행을 region_name store_name으로 합쳐서 반환해줘라. 
* * *
##### WHERE 조건 문법 
- = : 같다 
- !=,<> : 같지않다 
- < : 클때 <= : 크거나 같을때 
- AND : 여러조건 TRUE 1순위연산 
- OR : 하나의 조건만 맞아도 TRUE 2순위연산
- NOT :  부정조건 
* * *
##### LIKE : WHERE절에 사용되며 특정패턴을 검색할 때 사용 
- % : 0개 문자 혹은 여러개의 문자를 의미 
- _ : _한개당 1하나의 문자를 의미 
- NOT을 붙여서 사용할 수 있다.
> ###### LIKE 예제 
> - LIKE 'a%' : a로 시작하는 모든것 
> - LIKE 'a__%' : a로 시작하면서 최소길이가 3이상인 모든것 
> - LIKE '_r%' :  두번째자리에 r이들어가는 모든것 
* * *
##### IN : WHERE절에 사용되며 여러 값을 넣어줄 때 사용 
> ###### IN 예제 
> - SELECT * FROM Customers WHERE Country = 'Germany' OR Country = 'UK';
> - SELECT * FROM Customers WHERE Country IN ('Germany', 'UK'); 로 조금 더 가독성 좋게 변경가능하다.
* * *
##### IFNULL
-IFNULL(변수,명령) : 변수가 Null 이면 명령해라 
> ###### IFNULL 예제 
> - SELECT ANINAL_TYPE, IFNULL(NAME, 'No name'), ~~~~ : NAME값이 null 이면 No name으로 바꿔라. 
* * *
##### BETWEEN : WHERE절에 사용되며 조건범위를 지정할 때 사용 
* * *
##### LIMIT n : n만큼 데이터 개수를 위에서부터 return 한다.
##### LIMIT n, m :n에서부터 m만큼의 데이터 개수를 위에서부터 return 한다. 
- n,m선언을 하면 n은 n-1번째 배열을 추출한다. 
* * *
##### ORDER BY ASC|DESC (default : ASC)
- ORDER BY 테이블을 넣어서 테이블 기준으로 정렬이 가능하다.
- ORDER BY FILELD (열,열변수1,열변수2...열변수n)
- ORDER BY FILED 를 사용하면 내가원하는 변수들로 순서를 지정할 수 있다.

##### GROUP BY 
- 결과를 지정한 열에 따라서 그룹으로 묶어줄때 사용한다.

##### HAVING 
- GROUP BY 테이블에서 특정조건에 맞는 데이터만을 추출할때 사용한다.
* * *
##### NULL VALUE 
- SQL문 맨뒤에 IS NULL/NOT NULL을 사용한다.
- 조건연산자들로는 검색되지 않는 값들. 
- COUNT로도 체크가 되지 않는다.
* * *
##### ROUND, TRUNC
- 반올림과 버림 문법이다.
- 숫자뿐만이 아닌 날짜도 가능하다
- ROUND(변수,1): 소수첫번째자리에서 반올림 
- TRUNC(변수,-1): 십의자리에서 반올림 ( -는 자연수로간다.)
* * *
##### DATEDIFF 
- 기본폼은 DATEDIFF(interval, Start_DATE, End_DATE)로 사용한다. 
- interval에는 아래와 같은 형식자들이 들어간다.
- 날짜의 차이를 int형으로 반환한다
-    <img src="https://lh3.googleusercontent.com/-asKrL-jKwkA/V1kP84UiJLI/AAAAAAAAEFs/QCKX5hd89ro/s72-c/t-sql-date-diff%25255B2%25255D.png?imgmax=500" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="RubberDuck"></img>

##### DATE_FORMAT 
- 기본폼은 DATE_FORMAT(date, FORMAT)으로 사용한다.
- FORMAT은 아래와 같은 형식자들이 들어간다. 
- <img src="https://m-veloper.github.io/assets/img/database/2020/04/2020-04-28-database-42-02.png" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="RubberDuck"></img>
- date에는 NOW()같은 함수를 넣을 수 있다.
* * *
##### JOIN 
- 두 개나 그 이상으 ㅣ테이블의 행을 서로 결합하고자 할 때 사용 
- INNER JOIN : INNER는 default 이기에 생략을 할 수 있다. 
- LEFT JOIN : 기준점이 JOIN에 왼쪽 테이블을 기준으로 
- RIGHT JOIN : 기준점이 JOIN에 오른쪽 테이블을 기준으로 
- FULL OUTER JOIN : 기준점이 ON에서 언급한 값만 존재하면 왼쪽 오른쪽 다 포함이다.

##### UNION : 두개 이상의 질의 결과를 하나의 테이블로 합치고자할때 
- 기본적으로 중복값은 제거가 되므로 이 상황을 배제하기 위해서는 UNION ALL을 사용한다. 
