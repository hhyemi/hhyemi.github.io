---
title: Oracle - Error 정리 (ORA-)
tags: Oracle
key: page-202010251651
summary : 자주 일어나는 Oracle Error를 정리해보자 + 계속 추가
aside:
  toc: true
---
# 오라클 에러 정리 :no_entry_sign:
자주 일어나는 Oracle Error를 정리해보자
<br/>
<br/>

## ORA-00918: 열의 정의가 애매합니다.
테이블 JOIN 시 어느 테이블의 컬럼인지 정확하게 파악이 되지않는 경우(같은 컬럼명) 발생 <br/>
테이블명이 맞는지 확인하거나 컬럼명 앞에 A. B. 중복컬럼을 구분해준다.

<br/>

## ORA-01940: 현재 접속되어 있는 사용자는 삭제할 수 없습니다.
사용자를 삭제할때 현재 접속중이라 삭제가 안되는 경우 발생 <br/>

#### 사용자확인

```javascript
select sid,serial#,username,status from v$session where schemaname = '사용자아이디(대문자)';
```
![Image Alt 텍스트](/assets/images/oracleerror.png)

#### 프로세스 죽이기
```javascript
alter system kill session 'sid,serial#';
// alter system kill session '1521,9356';
```

#### 사용자 삭제
```javascript
drop user [사용자아이디] cascade;
```

<br/>

## ORA-01013: 사용자가 현재 작업의 취소를 요청했습니다.
Spring + mybatis 환경에서 발생하는 경우가 있다. <br/>
쿼리를 요청하고 시간이 오래걸려서 응답이 오지않아 작업을 취소하는 경우이다. <br/>

```xml
<insert id="query_test" parameterType="map" timeout="180">
...
</insert>
```

```timeout="180"```을 적어 타임아우스이 길이를 설정해주면 해결된다. <br/>
단위는 초(s)로 180은 3분이 된다.


<br/><br/><br/><br/>
