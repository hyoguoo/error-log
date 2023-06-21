## 키워드

- CORS

## 발생 시점

해당 도메인에 대해 설정을 열어두었으나 에러 발생

## 발생 에러

```
*** has sbeen blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.
```

## 해결 방법

`https://www.example.com`에 대해 설정을 열어두었으나 `https://example.com`으로 요청을 보내서 발생한 에러였다.  
브라우저 설정마다 `example.com`을 입력했을 때 `https://www.example.com`으로 자동으로 접속되는 경우도 있지만, 그대로 `http://example.com`으로 접속이 되어 발생한 에러였다.

### AS-IS

- 리다이렉트 설정을 요청하였으나 안되있던 상태

### TO-BE

- 리다이렉트 설정 재요청
- `https://example.com`에 대한 CORS 설정 추가
