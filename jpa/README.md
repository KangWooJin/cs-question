# jpa

## N+1

## getOne vs findById
```
- getOne, findById 차이
- getOne은 db에 조회를 lazy하게 요청하는 방식으로 사용할때 db query가 날라가고 만약 없는 데이터면 에러 발생
- findById는 db조회를 해서 데이터가 있는지 없는지 유저가 처리할 수 있게 하는 방식
```

## 양방향 관계에서 mappedby의 의미
```
- 관계의 주인
- mappedBy 설정을 해주지 않으면 양방향 관계라고 인식하지 않고 중간 테이블이 생기는 현상
- Foreign key가 생기는 테이블
- OneToMany에서 mappedby를 설정하는데, ManyToOne에 필드를 설정해서 중간 테이블이 생기지 않도록 하고 ManyToOne에서 OneToMany Entity의 키 값을 테이블에서 갖고 있음
```
