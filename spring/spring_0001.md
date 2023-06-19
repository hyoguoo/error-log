## 발생 시점

Spring 의존성 주입 시 자기 자신 주입하여 순환 참조 발생

## 발생 에러

```
Description:

The dependencies of some of the beans in the application context form a cycle:

┌──->──┐
|  callServiceV1
└──<-──┘
```

## 해결 방법

### AS-IS

--

### TO-BE

1. 방법 1

스프링 설정 파일에 다음과 같이 설정

```
spring.main.allow-circular-references=false
```

2. 방법 2

애초에 순환 참조를 하지 않도록 설계하는 것이 좋음