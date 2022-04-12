## ORM vs SQL
> Sequlize같은 ORM과 MySQL같은 데이터베이스의 차이가 무엇인가요?
> > DB를 JS로 다루느냐, SQL로 다루느냐

### SQL
#### 특징
> 관계형 DB를 다루기 위한 언어   
> 데이터 정의어: 테이블 생성/변경/삭제   
> 데이터 조작어: 테이블 검색, 데이터 삽입/수정/삭제   
> 데이터 제어어: 데이터에 대한 접근 및 사용 권한 관리
#### 장점
관계형 DB를 조작하는데 특화되어서 왠만한 조작은 다 가능
#### 단점
데이터베이스를 다루기 위한 별도의 언어를 학습해야 함

### ORM
> Object-Relational Mapping
#### 특징
> 자바스크립트 언어로 관계형 DB를 조작   
> 예시: sequelize-MySQL
#### 장점
SQL문을 배우지 않고도 관계형 DB 조작 가능 
#### 단점
1. 디테일한 조작이 어려울 수 있음   
2. spring 등 다른 프레임워크를 사용하게 될 경우 결국 SQL을 배워야 함   

### ODM
> Object-Document Mapping   
> 예시: mongoose-MongoDB
