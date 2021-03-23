---
title: Oracle - 컬럼타입 VARCHAR에서 CLOB로 변경
tags: Oracle
key: page-202103232005
summary : VARCHAR2 to CLOB
---

##  VARCHAR2 to CLOB
```sql
ALTER TABLE [테이블명] MODIFY ([바꿀컬럼명] CLOB)
```
위에있는 컬럼타입 바꾸는 쿼리를 돌리게 되면 **ORA-22858: 데이터유형의 변경이 부적당합니다**라고 오류가 뜨게된다.

## 해결
```sql
ALTER TABLE [테이블명] ADD ([추가컬럼명] CLOB);
UPDATE [테이블명] SET [추가컬럼명] = [바꿀컬럼명];
COMMIT;
ALTER TABLE [테이블명] DROP COLUMN [바꿀컬럼명];
ALTER TABLE [테이블명] RENAME COLUMN [추가컬럼명] TO [바꿀컬럼명];
```
- 테이블에 CLOB타입인 TEMP 컬럼을 하나 생성한다.
- 바꿀컬럼의 데이터를 TEMP컬럼에 넣어준다.
- 커밋
- 바꿀 컬럼을 삭제해준다. (데이터를 다 옮겼기 때문에)
- TEMP컬럼의 이름을 바꿀 컬럼명으로 변경한다.

<br/><br/>
