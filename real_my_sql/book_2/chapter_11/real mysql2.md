---
_filters: []
_contexts: []
_links: []
_sort:
  field: name
  asc: true
  group: false
---

대소문자 구분, 문자열 표기 방법 등과 같은 SQL 작성 규칙은 MySQL 서버의 시스템 설정에 따라 달라진다.
MySQL 서버의 시스템 설정이 쿼리에 어떤 영향을 주는지 살펴보자.
MySQL의 예약어에 대해 살펴보고 주의사항도 같이 알아보자.
## 11.1.1 SQL 모드
**SQL의 동작 방식을 제어하는 설정 옵션**
- ONLY_FULL_GROUP_BY
  GROUP BY 구문의 동작 방식을 제어하는 옵션이다.
  GROUP BY 절에 포함되지 않은 칼럼을 SELECT 절에서 사용할수 있냐 없냐를 제어한다.
  비활성화시 사용할 수 있고 활성화시 사용할 수 없다.
- STRICT_ALL_TABLES & STRICT_TRANS_TABLES
  INSERT, UPDATE 문장으로 데이터를 변경하는 경우 칼럼의 타입과 저장되는 값의 타입이 다를 때 자동으로 타입 변경을 수행한다.(암묵적 형변환) 이때 타입이 적절히 변환되기 어렵거나 칼럼에 저장될 값이 없거나 값의 길이가 칼럼의 최대 길이보다 큰 경우 에러 또는 경고를 발생시킨다.
  STRICT_TRANS_TABLES 옵션은 트랜잭션 기반 테이블의 경우에는 모두 에러처리이고, 비 트랜잭션 기반 테이블은 에러 또는 경고 처리이며 STRICT_ALL_TABLES 옵션은 트랜잭션 기반 테이블, 비 트랜잭션 기반 테이블 구분 없이 모두 에러 처리이다.
- ANSI_QUOTES
  이 옵션은 싱글 쿼트('), 더블 쿼트("), 백틱(\`)의 사용 방법이 변경된다.
	- 옵션 비활성화
		- 더블 쿼트 (") : 문자열 **리터럴**
		- 싱글 쿼트 (') : 문자열 리터럴
		- 백틱 (\`) : 식별자 (테이블 이름, 컬럼 이름 등)
	- 옵션 활성화
		- 더블 쿼트 (") : 식별자 (테이블 이름, 컬럼 이름 등)
		- 싱글 쿼트 (') : 문자열 리터럴
		- 백틱 (\`) : 식별자 (테이블 이름, 컬럼 이름 등)
- PIPE_AS_CONCAT
  파이프(|) 문자를 BIT OR 연산자로 사용할지 문자열 연결 연산자(CONCAT)로 사용할지 제어하는 옵션이다.
  비활성화시 BIT OR 연산자, 활성화시 문자열 연결 연산자(CONCAT)으로 사용된다.
- PAD_CHAR_TO_FULL_LENGTH
  
- NO_ZERO_IN_DATE
- NO_ZERO_DATE
- ERROR_FOR_DIVISION_BY_ZERO
- NO_ENGINE_SUBSTITUTION
## 11.1.2 영문 대소문자 구분
## 11.1.3 MySQL 예약어

---
- 11.2 매뉴얼의 SQL 문법 표기를 읽는 방법

---
- 11.3 [[MySQL 연산자와 내장 함수]]
	- 11.3.1 [[리터럴 표기법 문자열]]
	- 11.3.2 [[MySQL 연산자]]
		- 11.3.2.9 [[IN 연산자]]
	- 11.3.3 [[MySQL 내장 함수]]
		- 11.3.3.1 [[NULL 값 비교 및 대체(IFNULL, ISNULL)]]
		- 11.3.3.2 [[현재 시각 조회(NOW, SYSDATE)]]
		- 11.3.3.3 [[날짜와 시간의 포맷(DATE_FORMAT, STR_TO_DATE)]]
		- 11.3.3.4 [[날짜와 시간의 연산(DATE_ADD, DATE_SUB)]]
		- 11.3.3.5 [[타임스탬프 연산(UNIX_TIMESTAMP, FROM_UNIXTIME)]]
		- 11.3.3.6 [[문자열 처리(RPAD, LPAD, RTRIM, LTRIM, TRIM)]]
		- 11.3.3.7 [[문자열 결합(CONCAT)]]
		- 11.3.3.8 [[GROUP BY 문자열 결합(GROUP_CONCAT)]]
		- 11.3.3.9 [[값의 비교와 대체(CASE WHEN ... THEN ... END)]]
		- 11.3.3.10 [[타입의 변환(CAST, CONVERT)]]
		- 11.3.3.11 [[이진값과 16진수 문자열(Hex String) 변환(HEX, UNHEX)]]
		- 11.3.3.12 [[암호화 및 해시 함수(MD5, SHA, SHA2)]]
		- 11.3.3.13 [[처리 대기(SLEEP)]]
		- 11.3.3.14 [[벤치마크(BENCHMARK)]]
		- 11.3.3.15 [[IP 주소 변환(INET_ATON, INET_NTOA)]]
		- 11.3.3.16 [[JSON 포맷(JSON_PRETTY)]]
		- 11.3.3.17 [[JSON 필드 크기(JSON_STORAGE_SIZE)]]
		- 11.3.3.18 [[JSON 필드 추출(JSON_EXTRACT)]]
		- 11.3.3.19 [[JSON 오브젝트 포함 여부 확인(JSON_CONTAINS)]]
		- 11.3.3.20 [[JSON 오브젝트 생성(JSON_OBJECT)]]
		- 11.3.3.21 [[JSON 칼럼으로 집계(JSON_OBJECTAGG & JSON_ARRAYAGG)]]
		- 11.3.3.22 [[JSON 데이터를 테이블로 변환(JSON_TABLE)]]
- 11.4 [[SELECT]]
	- 11.4.1 [[SELECT 절의 처리 순서]]
	- 11.4.2 [[WHERE 절과 GROUP BY 절, ORDER BY 절의 인덱스 사용]]
		- 11.4.2.1 [[인덱스를 사용하기 위한 기본 규칙]]
		- 11.4.2.2 [[WHERE 절의 인덱스 사용]]
		- 11.4.2.3 [[GROUP BY 절의 인덱스 사용]]
		- 11.4.2.4 [[ORDER BY 절의 인덱스 사용]]
		- 11.4.2.5 [[WHERE 조건과 ORDER BY(또는 GROUP BY) 절의 인덱스 사용]]
		- 11.4.2.6 [[GROUP BY 절과 ORDER BY 절의 인덱스 사용]]
		- 11.4.2.7 [[WHERE 조건과 ORDER BY 절, GROUP BY 절의 인덱스 사용]]
	- 11.4.3 [[WHERE 절의 비교 조건 사용 시 주의사항]]
		- 11.4.3.1 [[NULL 비교]]
		- 11.4.3.2 [[문자열이나 숫자 비교]]
		- 11.4.3.3 [[날짜 비교]]
			- 11.4.3.3.1 [[DATE 또는 DATETIME과 문자열 비교]]
			- 11.4.3.3.2 [[DATE와 DATETIME의 비교]]
			- 11.4.3.3.3 [[DATETIME과 TIMESTAMP의 비교]]
			- 11.4.3.3.4 [[Short-Circuit Evaluation]]
	- 11.4.4 [[DISTINCT]]
	- 11.4.5 [[LIMIT n]]
	- 11.4.6 [[COUNT]]
	- 11.4.7 [[JOIN]]
		- 11.4.7.1 [[JOIN의 순서와 인덱스]]
		- 11.4.7.2 [[JOIN 칼럼의 데이터 타입]]
		- 11.4.7.3 [[OUTER JOIN의 성능과 주의사항]]
		- 11.4.7.4 [[JOIN과 외래키(FOREIGN KEY)]]
		- 11.4.7.5 [[지연된 조인(Delayed Join)]]
		- 11.4.7.6 [[래터럴 조인(Lateral Join)]]
		- 11.4.7.7 [[실행 계획으로 인한 정렬 흐트러짐]]
	- 11.4.8 [[GROUP BY]]
		- 11.4.8.1 [[WITH ROLLUP]]
		- 11.4.8.2 [[레코드를 칼럼으로 변환해서 조회]]
			- 11.4.8.2.1 [[레코드를 칼럼으로 변환]]
			- 11.4.8.2.2 [[하나의 칼럼을 여러 칼럼으로 분리]]
	- 11.4.9 [[ORDER BY]]
		- 11.4.9.1 [[ORDER BY 사용법 및 주의사항]]
		- 11.4.9.2 [[여러 방향으로 동시 정렬]]
		- 11.4.9.3 [[함수나 표현식을 이용한 정렬]]
	- 11.4.10 [[서브쿼리]]
		- 11.4.10.1 [[SELECT 절에 사용된 서브쿼리]]
		- 11.4.10.2 [[FROM 절에 사용된 서브쿼리]]
		- 11.4.10.3 [[WHERE 절에 사용된 서브쿼리]]
			- 11.4.10.3.1 [[동등 또는 크다 작다 비교]]
			- 11.4.10.3.2 [[IN 비교( IN(subquery) )]]
			- 11.4.10.3.3 [[NOT IN 비교( NOT IN(subquery) )]]
		- 11.4.11 [[CTE(Common Table Expression)]]
			- 11.4.11.1 [[비 재귀적 CTE(Non-Recursive CTE)]]
			- 11.4.11.2 [[재귀적 CTE(Recursive CTE)]]
			- 11.4.11.3 [[재귀적 CTE(Recursive CTE) 활용]]
		- 11.4.12 [[윈도우 함수(Window Function)]]
			- 11.4.12.1 [[쿼리 각 절의 실행 순서]]
			- 11.4.12.2 [[윈도우 함수 기본 사용법]]
## JOIN
## GROUP BY
## ORDER BY
## 서브쿼리
## CTE(Common Table Expression)
## 윈도우 함수(Window Function)
## 잠금을 사용하는 SELECT

---
# INSERT
## 고급 옵션
## LOAD DATA 명령 주의 사항
## 성능을 위한 테이블 구조

---
# UPDATE와 DELETE
## UPDATE ... ORDER BY ... LIMIT n
## JOIN UPDATE
## 여러 레코드 UPDATE
## JOIN DELETE

---
# 스키마 조작(DDL)
## 온라인 DDL
## 데이터베이스 변경
## 테이블 스페이스 변경
## 테이블 변경
## 칼럼 변경
## 인덱스 변경
## 테이블 변경 묶음 실행
## 프로세스 조회 및 강제 종료
## 활성 트랜잭션 조회

---
# 쿼리 성능 테스트
## 쿼리의 성능에 영향을 미치는 요소