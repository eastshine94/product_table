# 상품 테이블 만들기(Frontend Junior Test)

## 1. 미션 내용
> 채용 과제로 수행한 상품 테이블을 만드는 미션입니다. 미션의 내용은 다음과 같습니다.

### 1) 기술 스택
1. Typescript
2. VueJS
3. NuxtJS

### 2) 평가 목록
- 상품 테이블
  - [ ] 한 페이지에 나오는 아이템 수를 제어할 수 있는가
  - [ ] 현재 페이지를 확인할 수 있고, 특정페이지로 이동할 수 있는가(페이지네이션)
  - [ ] 테이블 헤더를 클릭하여 정렬된 결과를 얻을 수 있는가
- 상품필터
  - [ ] 필드, 연산자, 값을 제대로 입력할 수 있는가
  - [ ] 여러개의 조건필터를 중첩하여 생성할 수 있는가
  - [ ] 중간에 필터를 삭제할 수 있는가
  - [ ] 필터를 이용해서 생산된 검색쿼리가 필터의 내용과 일치하는가
  - [ ] 검색쿼리로 서버의 데이터를 잘 가져오는가
  - [ ] 필터 수정시 마다 적절하게 데이터가 변경되는가
- 퍼블리싱
  - [ ] 필터를 직관적으로 사용할 수 있는가
  - [ ] 상품을 로딩하는 동안 로딩중 표시가 있는가
  - [ ] 모바일 화면(width: 640px)에서도 테이블의 내용을 확인할 수 있는가
  - [ ] 모바일 화면에서도 상품필터를 수정하는데에 무리가 없는가
- 코드 스타일
  - [ ] 변수명, 메소드명은 적절한가
  - [ ] 작명 스타일(camelCase, snakeCase 등)은 일관적인가
  - [ ] 사용되지 않는 변수, 메서드가 없는가
  - [ ] 제출 결과물에 console.log가 포함되지 않았는가

가산점

- [ ] 검색된 내용을 그래프로 요약할 수 있는가([Toast Chart](https://ui.toast.com/tui-chart/) 이용)
- [ ] 새로고침을 했을 때, 마지막에 작성했던 검색쿼리를 남길 수 있는가
- [ ] 누군가에게 URL로 공유했을 때, 검색쿼리를 포함해서 공유할 수 있는가
- [ ] 대기중인 경우 화면 전환(또는 애니메이션)을 이용하여 로딩 시간을 지루하지 않게 하는가

## 2. 구현

### 1) 프로세스

미션에서 요구하는 사항을 수행하기 위해 다음의 프로세스로 웹 페이지를 구성했습니다.

![순서도](https://user-images.githubusercontent.com/41350459/86533033-3ef3d700-bf09-11ea-88ef-4fff4bb76d86.png)

- 사용자가 버튼을 누르는 등의 action을 취하면, URI 쿼리를 변경시킵니다. 
- 쿼리의 변경에 따라 store의 state 값을 변경합니다. 
- 그 후 store에 state 값을 이용하여 API를 호출할 URI를 얻습니다. 
- 이 URI를 통해 데이터 값을 불러오게 됩니다. 
- 만약 올바르게 데이터가 들어오면 상품 테이블을 변경하고, 그렇지 않다면 에러 페이지로 이동하게 됩니다.

### 2) 웹 페이지 구현

위의 프로세스를 준수하며 다음과 같이 웹 페이지를 제작하였습니다.

#### 2-1 필터
![필터](https://user-images.githubusercontent.com/41350459/86557211-78235a00-bf90-11ea-81ac-c6ba84d173b6.gif)

- 판매가, 판매원가, 등록 시기를 기준으로 상품을 필터를 할 수 있습니다.
- 필터가 적용되면 아래에 적용된 필터 목록을 보여줍니다.
- X를 클릭하여 적용된 필터를 제거할 수 있습니다.

#### 2-2 상품 수량
![상품수량](https://user-images.githubusercontent.com/41350459/86557195-6e99f200-bf90-11ea-8105-a62a7c61047a.gif)

- 테이블에 나오는 아이템 수를 제어할 수 있습니다.
- 직접 입력을 선택하여 아이템 수를 사용자가 직접 입력하여 제어할 수 있습니다.

#### 2-3 페이지네이션
![페이지네이션](https://user-images.githubusercontent.com/41350459/86557208-76f22d00-bf90-11ea-9ac9-7075b2f86386.gif)


- 현재 페이지를 확인할 수 있고, 특정페이지로 이동할 수 있습니다.
- 이전, 다음, 처음, 마지막 페이지로 이동할 수 있습니다.

#### 2-4 테이블
![테이블](https://user-images.githubusercontent.com/41350459/86557205-75c10000-bf90-11ea-8505-fbad80d2c761.gif)

- 테이블 헤더를 클릭하여 정렬된 결과를 얻을 수 있습니다.
- 테이블 헤더의 화살표 아이콘을 통해 어떤 기준으로 오름차순, 내림차순 정렬되어 있는지 확인할 수 있습니다.

#### 2-5 차트
![차트](https://user-images.githubusercontent.com/41350459/86557204-73f73c80-bf90-11ea-8ec2-2f6a6c3afd2c.gif)


- 차트 버튼을 클릭하여 검색된 상품의 월별 상품 등록 가격을 box plot으로 확인 할 수 있습니다.