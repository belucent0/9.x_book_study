ORDER BY 절에 문자열 상수를 사용하는 경우 옵티마이저가 ORDER BY 절 자체를 무시한다.
```sql
SELECT ...
ORDER BY "name";
```