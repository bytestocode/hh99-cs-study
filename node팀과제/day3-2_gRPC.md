## gRPC 프로토콜 통신
> HTTP/HTTPS 프로토콜이 아닌 gRPC 프로토콜로 통신하는 서버 프로그램은    
> API 서버라고 부를 수 있을까요? (배포된 환경, 구현된 기능은 동일)

### gRPC 프로토콜
> RPC: Remote Procedure Call의 약어   
> gRPC: 구글에서 만든 RPC

### 비교
클라이언트-서버 간 데이터를 교환할 때,   
일반적으로 XML, JSON을 데이터 형식으로 사용하듯이   
gRPC에서는 프로토(프로토콜 버퍼)를 사용합니다.

### 특징
1. 크로스플랫폼 (모바일 - 서버)
2. 크로스랭귀지 (C++, Go, Java, Python, Javascript 등등)
3. 빠른 속도 (HTTP/2, binary-type)

### 결론 
> gRPC = 클라이언트의 요청에 응답하기 위한 방법   
> 클라이언트의 요청에 응답하기 위한 방법 = API   
> gRPC = API
> 