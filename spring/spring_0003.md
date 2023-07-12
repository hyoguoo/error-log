## 키워드

- 스프링(Spring)
- QueryDSL

## 발생 시점

`fetchOne()` 으로 단건 조회 시 에러 발생

### 환경

- MacOS
- Spring Boot 3.1.1
- Querydsl 5.0.0
- java 17

## 발생 에러

```
com.querydsl.core.NonUniqueResultException: jakarta.persistence.NonUniqueResultException: query did not return a unique result: 4

	at com.querydsl.jpa.impl.AbstractJPAQuery.fetchOne(AbstractJPAQuery.java:331)
...
```

## 해결 방법

조회 된 결과가 2개 이상이기 때문에 fetchFirst() 혹은 where 절을 추가하여 단 건만 조회하도록 수정

### AS-IS

```java
Member fetchOne=queryFactory
        .selectFrom(member)
        .fetchOne();
```

### TO-BE

```java
Member fetchOne=queryFactory
        .selectFrom(member)
        .where(member.username.eq("member1"))
        .fetchOne();
```

혹은

```java
Member fetchFirst = queryFactory
        .selectFrom(member)
        .fetchFirst();
```