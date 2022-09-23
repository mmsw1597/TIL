## Middleware
HTTP 요청과 응답 사이에서 단계별 동작을 수행해주는 함수.

## Middleware 작성
1. req, res, next를 가진 함수를 작성하면 해당 함수는 미들웨어로 동작 가능함.
2. req는 HTTP 요청을 처리하는 객체
3. res는 HTTP 응답을 처리하는 객체
4. next는 다음 미들웨어를 실행하는 함수.

## Route Handler
1. 이또한 미들웨어의 한 종류
2. 라우팅 함수에 적용된 미들웨어
3. path parameter를 사용 가능.

