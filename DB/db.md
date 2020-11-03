# 데이터베이스

<br/>

- [데이터베이스란?](https://github.com/yujin122/TIL/blob/master/DB/db.md#데이터베이스)
- [무결성(Integrity)](https://github.com/yujin122/TIL/blob/master/DB/db.md#무결성Integrity)
- [쿼리문](https://github.com/yujin122/TIL/blob/master/DB/db.md#쿼리문)
- [그룹함수](https://github.com/yujin122/TIL/blob/master/DB/db.md#그룹함수)
- [조인(Join)](https://github.com/yujin122/TIL/blob/master/DB/db.md#join-on)
- [시퀀스(sequence)](https://github.com/yujin122/TIL/blob/master/DB/db.md#시퀀스sequence)
- [서브 쿼리](https://github.com/yujin122/TIL/blob/master/DB/db.md#서브쿼리)
- [group by - having절](https://github.com/yujin122/TIL/blob/master/DB/db.md#groupby-having절)
- [View](https://github.com/yujin122/TIL/blob/master/DB/db.md#view)
- [트랜잭션](https://github.com/yujin122/TIL/blob/master/DB/db.md#트랜잭션transacion)
<br/>

## 데이터베이스
구조화된 데이터의 집합

- 여러 사람과 실시간으로 공유하여 사용
- 효율적인 데이터관리
- 효율적인 데이터 검색
- 일관성 있는 방법으로 데이터 관리
- 데이터 누락 및 중복제거
<br/>

## DBMS(data base management system)

> 응용프로그램 - DBMS - 데이터베이스

컴퓨터에 저장되는 데이터 베이스를 관리해주는 소프트웨어 시스템
 <br/>
 
## DB 테이블에 들어가는 주요 자료형(data type)

1. **num**(*n, n1*) :  n은 전체 자릿수, n1은 소숫점 자릿수, n - n1은 정수 자릿수
2. **char**(*n*) : 문자열이 n개가 저장되는 자료형 ==> 고정 자료형

 3. **varchar**(*n*) : 문자열이 n개가 저장되는 자료형 ==> 현재 사용하지 않는 자료형

 4. **varchar2**(*n*) : 문자열이 n개가 저장되는 자료형 ==> 가변 자료형
			               한글은 무조건 한 글자당 2byte씩 소모.
 
 5. **data** : 날짜가 저장되는 자료형 ==> 시스템의 현재 날짜 및 시간이 저장
<br/>

## 무결성(Integrity)
데이터베이스에 저장된 데이터 값과 그것이 표현하는 현실 세계의 실제 값이 일치하는 정확성을 의미
<br/>
<br/>

### 무결성 제약조건
데이터베이스에 저장된 데이터의 정확성을 보장하기 위해서 정확하지 않는 데이터가 데이터베이스 내에 저장되는 것을 방지하기 위한 조건
<br/>

### 제약조건 종류
1. **unique** 제약 조건 : 중복이 되면 안되는 조건
2. **not null** 제약 조건 : 공백을 허용하지 않는 조건
3. **check** 제약 조건 : 특정한 값이 아닌 데이터가 들어오지 못하게 하는 조건<br/>

	형식) 

		constraint 체크이름 check(컬럼명 in(특정데이터목록))

4. **primary key** 제약 조건 : unique + not null 제약 조건 <br/>
	-> 기본키는 해당 테이블을 대표하는 컬럼으로서의 역할을 수행, 다른 테이블에서 외래키들이 참조할 수 있는 키로서의 자격을 가진다.
5. **foreign key**(외래키) : 다른 테이블의 필드(컬럼)를 `참조`해서 무결성을 검사하는 제약 조건<br/>

	형식) 

	    references 참조하는테이블(컬럼명)
<br/>

- **참조키** : 부모테이블의 컬럼을 이야기 함
- **외래키** : 자식테이블의 컬럼을 이야기 함

<br/>

## 쿼리문

### 테이블 만들기

형식)

    create table 테이블 이름(
    			컬럼명1 자료형(크기) (제약조건),
    			컬럼명2 자료형(크기) (제약조건),
    			컬럼명3 자료형(크기) (제약조건),
    			...
    );
<br/>

### 테이블 수정
#### 컬럼 추가

    alter table 테이블 이름 add(컬럼명 데이터타입(크기) 제약조건);

#### 컬럼 수정(자료형 수정)

    alter table 테이블 이름 modify(컬럼명 데이터타입(크기));

#### 컬럼 삭제

    alter table 테이블 이름 drop column 컬럼명;
<br/>

### 데이터 추가

형식1)

    insert into 테이블이름 values (컬럼1 데이터값, 컬럼2 데이터값, 컬럼3 데이터값, ...);

형식2)

    insert into 테이블이름(컬럼1, 컬림3, ...) values(컬럼1 데이터값, 컬럼3 데이터값);

> 제약조건이 primary key와 not null인 컬럼은 꼭 포함하여야 한다.

<br/>

### 데이터 수정

    update 테이블이름 set 컬럼이름 = 컬럼수정내용 where 기본키로 설정된 컬럼명 = 수정하려는 컬럼 데이터;
<br/>

### 데이터 삭제

    delete from 테이블이름 where 기본키로 설정된 컬럼명 =  삭제하려는 컬럼 데이터;
<br/>

### 데이터 검색

형식)

    select 컬럼명1, 컬럼명2, ...
    from 테이블명
    where 조건;

#### select
해당 `컬럼명`들의 데이터를 보여준다.

#### from 
해당 `테이블`의 데이터를 보여준다.

#### where
해당 `조건`에 맞는 데이터만 보여준다.
<br/>

**연산자**

||  |
|--|--|
| = | 조건이 같은가? |
| < | 조건이 작은가? |
| <= | 조건이 작거나 같은가? |
| > | 조건이 큰가? |
| >= | 조건이 크거나 같은가? |
| != | 조건이 같지 않은가? |
| <> | 조건이 같지 않은가? |
| between A and B | A와 B 사이에 있는가? |
| not between A and B | A와 B 사이에 없는가? |
| in(list) | list 값 중 어느 하나와 일치하는가? |
| not in(list) | list 값과 일치하지 않는가? |
<br/>

### 기타

#### -  nvl() 함수
null 값을 특정한 값으로 변경, 모든 데이터 타입에 적용이 가능하다.

##### 형식)

    nvl(null 값이 들어 있는 컬럼명, 변경할 값)

#### - nvl2() 함수

##### 형식) 

    nvl2(컬럼명, expr1, expr2)

컬럼명의 값이 null이 아닌 경우에는 expr1을 반환, null인 경우에는 expr2를 반환

#### - as
컬럼 제목에 `이름을 변경`하는 키워드, 컬럼명 바로 뒤에 사용

#### - distinct
`중복을 제거`하는 키워드, distinct 뒤에 나오는 컬럼들은 모두 적용

#### - literal 문자열
컬럼명이나 별칭이 아닌 select 목록에 포함되는 문자, 표현식 숫자를 의미

- 날짜나 문자열인 경우 단일 인용부호('')를 사용해야 한다.

##### ex)

    "KING 사원의 연봉은 60000 입니다."
    
    select ename || '사원의 연봉은' || sal*12 || '입니다.' "사원의 연봉" from emp;
     

 #### - like 연산자
 검색하는 연산자

- where name **like '%S%**' : 해당 컬럼에 S자를 포함하는 문자 검색
- where name **like '%S'** : 해당 컬럼에 마지막 글자가 S자인 문자 검색
- where name **like 'S%'** : 해당 컬럼에 첫 글자가 S자인 문자 검색
- where name **like '__S%'** : 해당 컬럼에 세번째 글자가 S자인 문자 검색

#### - Order by
자료를 정렬하여 나타낼 때 필요한 구문

> select 구문의 맨 마지막에 위치

- **asc** : 오름차순 정렬, default 값(생략가능)
- **desc** : 내림차순 정렬

      select 컬럼명1, 컬럼명2, ... 
      from 테이블명 
      where 조건 
      order by 컬럼명 acs(desc)

<br/>

## 그룹함수
여러 행 또는 테이블 전체에 대하여 함수가 적용되어 하나의 결과 값을 가져오는 함수

1. **avg**() : 평균값을 구하는 함수
2. **count**() : 행의 갯수를 구하는 함수
3. **max**() : 최댓값을 구하는 함수
4. **min**() : 최솟값을 구하는 함수
5. **sum**() : 총합을 구하는 함수

 형식)

		select avg(컬럼명) 
		from 테이블명
		where 조건;
<br/>

## Join on

`테이블과 테이블을 연결`하여 특정한 데이터를 얻고자 할 때 사용한다.

- 데이터의 중복을 막기 위해 두 개 이상의 테이블에 정보를 나누어 저장하는데 두 개의 테이블을 통해 원하는 정보를 얻으려면 여러 번 질의를 해야 한다. <br/>
이를 join 을 사용해 `테이블을 결합`하여 원하는 결과를 얻어낼 수 있게 한다. 
<br/>

### 조인의 종류
### 1. Cross Join
두 개 이상의 테이블이 조인될 때 조건이 없이 테이블의 결합이 이루어지는 조인

### 2. Equi Join
조인의 대상이 되는 두 테이블에서 `공톡적으로 존재하는 컬럼의 값이 일치되는 행`을 연결하여 결과를 생성

형식)

    select 컬럼명1, 컬럼명2, 컬럼명3, ...
    from 테이블1 join 테이블2
    on 테이블1.공통컬럼명 = 테이블2.공통컬럼명
    where 조건;

> 컬럼의 이름이 같으면 혼동이 오기 때문에 컬럼 이름 앞에 테이블의 이름을 기술.

### 3. Self Join
`자기 자신 테이블과 조인`을 맺는 것

-  from  절 다음에 테이블 이름을 나란히 두 번 기술할 수 없기 때문에 테이블에 `별칭을 붙여 사용`

형식)

    select 컬럼명1, 컬럼명2, 컬럼명3, ...
    from 테이블 별칭1, 테이블 별칭2
    where 조건(ex. 별칭1.컬럼명 = 별칭2.컬럼명)

### 4. Outer Join
2개 이상의 테이블이 조인될 때 어느 한쪽 테이블에 해당하는 데이터가 존재하는데 다른쪽 테이블에는 데이터가 존재하지 않는 경우 그 데이터가 출력되지 않는 문제점을 해결하기 위해 사용되는 조인 기법

형식)

    select 컬럼명1, 컬럼명2, 컬럼명3, ...
    from 테이블 별칭1, 테이블 별칭2
    where 별칭1.컬럼명 = 별칭2.컬럼명(+)

정보가 부족한 테이블의 컬럼 뒤에 `(+) 기호`를 붙여서 사용
<br/><br/>

## 시퀀스(sequence)
`순번`을 부여할 때 사용하는 문법

형식)

    create sequence 시퀀스이름
    start with n				(n : 시작 번호 설정 - 기본값 1)
    increment by n				(n : 증가 번호 설정 - 기본값 1)
    maxvalue n					(n : 최대 번호 설정)
    minvalue n					(n : 최소 번호 설정)
    cache / nocache				(시퀀스의 값을 빠르게 설정하기 위해 캐쉬 메모리 사용 여부)
<br/>

    insert into 테이블이름 values(시퀀스이름.nextval, 데이터값1, 데이터값2, ...);
    -- nextval : 다음 번호
<br/>

## 서브 쿼리
`쿼리문 안에 또 다른 쿼리문`이 존재하는 쿼리문

- 서브쿼리는 메인쿼리에 포함되는 종속적인 관계
- 서브 쿼리는 `괄호`로 묶어서 사용
- 서브 쿼리 안에 order by 절을 사용할 수 없음
- `연산자 오른쪽`에 사용
<br/>

형식)

안쪽에 있는 쿼리문을 실행 후, 그 결과값을 가지고 바깥쪽 쿼리문을 실행

    select 컬럼명1, 컬럼명2, ...
    from 테이블명
    where 컬럼명 > (select 컬럼명 from 테이블명 where 조건);
<br/>

## group by - having절
<br/>

### group by

특정 컬럼을 기준으로 집계를 구하는데 많이 사용
<br/>

형식)

    select 컬럼명1, 그룹함수(컬럼명), ...
    from 테이블명
    group by 그룹으로 묶을 컬럼명

ex)

    select deptno, count(*)
    from emp
    group by deptno;
<br/>

### having
`group by 절`의 결과에 조건을 주어서 `제한`을 할 때 사용
<br/>

형식)

    select 컬럼명1, 그룹함수(컬럼명), ...
    from 테이블명
    group by 그룹으로 묶을 컬럼명
    having 조건

ex)

    select deptno, count(*)
    from emp
    group by deptno
    having count(*) >= 2;
<br/>

## View
물리적인 테이블에 근거한 `논리적인 가상의 테이블`

- 실질적으로 데이터를 저장하고 있지 않음
- 테이블과 유사하며 테이블처럼 사용이 가능
- 물리적인 공간이 필요 없음
- 뷰에 데이터 삽입 시 실제 테이블에 데이터가 삽입이 됨

### 사용 이유

> 보안 관리를 위해 사용 
> 
> 사용자의 편의성을 위해 사용

<br/>

형식)

    create view 뷰이름
    as
    서브쿼리

#### ex)

    create view emp_view
    as
    select * from emp

<br/>

* 읽기 전용 View <br/>
-> 쿼리문 맨 마지막에 `with read only` 작성
<br/>

## 트랜잭션(Transaction)
SQL 명령문들을 하나의 `논리적인 작업 단위로 처리`하는 것

- 데이터의 일관성을 유지하면서 데이터의 안정성을 보장하기 위해서 사용

### 명령어
1. **commit** : 모든 작업을 정상적으로 처리하겠다고 `확정`하는 명령어

2. **rollback** : 작업 중에 문제가 	발생했을 때 트랜잭션 처리 과정에서 발생한 변경사항을 취소하여 `이전 상태로 되돌리는` 명령어, 이전에 commit한 곳까지만 복구 가능
3. **savepoint** : 사용자가 트랜잭션 중간 단계에서 포인트를 지정하여 트랜잭션 내의 특정 `savepoint까지 rollback` 할 수 있게 하는 것
<br/>
형식) 

	    savepoint  세이브포인트이름;
	    rollback to 세이브포인트이름;
