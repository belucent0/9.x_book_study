MySQL 엔진의 쿼리 실행기에서 데이터를 쓰거나 읽어야 할 때에 스토리지 엔진에 요청을 한다.

- 핸들러 요청
	- MySQL 엔진에서 스토리지 엔진에게 보내는 데이터 I/O 요청
	- 대부분 MySQL엔진의 쿼리 실행기에서 요청
- 핸들러 API
	- MySQL 엔진, 스토리지 엔진 간의 데이터 교환을 위한 인터페이스

- 핸들러 API를 통한 작업 확인
```SQL
SHOW GLOBAL STATUS LIKE 'Handler%';
```