![[Pasted image 20250111132153.png]]

MySQL 서버는 프로세스 기반이 아니라 스레드 기반으로 작동한다.
스레드는 크게 포그라운드 스레드와 백그라운드 스레드로 구분할 수 있다.

MySQL 서버에서 실행 중인 스레드의 목록 확인
```SQL
SELECT thread_id, name, type, processlist_user, processlist_host
FROM performance_schema.threads ORDER BY type, thread_id;
```

목록 중 `one_connection` 스레드가 사용자의 요청을 처리하는 포그라운드 스레드다.