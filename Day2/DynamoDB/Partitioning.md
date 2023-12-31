### 파티셔닝
파티셔닝은 데이터베이스에서 데이터를 분산하여 저장하는 방법 중 하나로, 대용량 데이터를 처리하고 확장성을 높이는데 사용됩니다.

DynamoDB 내에는 해쉬 함수가 존재합니다.  

파티션 키는 해쉬 함수를 거쳐서 데이터를 저장할 파티션을 결정 합니다.  

동일한 파티션 키를 지닌 데이터는 물리적으로 가까운 위치에 저장됩니다.  

이때 데이터를 구분하기 위해 정렬 키를 사용합니다.  

정렬 키를 사용하면 동일한 파타션에 저장된 데이터는 정렬 키를 기준으로 저장됩니다.

### 파티션 키
물리적인 공간인 파티션을 구분하기 위한 키 입니다.  

스케일이 아무리 커져도 주소를 알고 있어서 데이터를 빠르게 가져올 수 있습니다.  

파티션 키로는 일치하는 값만 가져올 수 있고 `=` `>` `<` 등의 범위지정 방식 검색은 지원하지 않습니다.

### 정렬 키
파티션 안에서 데이터를 정렬하기 위한 키 입니다.  

DynamoDB에서는 Number, Binary, String 타입을 지원합니다.  

단순 정렬이기 때문에 파티션 사이즈가 커져도 데이터를 빠르게 가져올 수 있습니다.  

파티션 키와 달리 범위지정 방식 검색을 지원합니다.  

하지만 정렬 키만 가지고는 검색할 수 없습니다.

### 적절한 예
고객 정보를 저장하는 NoSQL 데이터베이스를 가정하겠습니다.

```
Partition Key: "CustomerID"
Sort Key: "Timestamp"
```

이 예시에서는 "CustomerID"가 파티션 키이며, 같은 "CustomerID" 값을 가진 모든 데이터가 동일한 파티션에 저장됩니다.  

"Timestamp"는 각 파티션 내에서 데이터를 정렬하는 데 사용됩니다.  

이러한 파티셔닝은 고객 별로 데이터를 구분하고, 고객의 데이터를 시간 순으로 정렬하여 쿼리할 수 있게 해줍니다.

### 부적절한 예
고객 정보를 저장하는 데이터베이스에서 파티셔닝에 사용하기 부적절한 예시는 아래와 같습니다.

```
Partition Key: "City"
Sort Key: "CustomerID"
```

이 예시에서 "City"를 파티션 키로 사용하면, 동일한 도시에 속하는 모든 데이터가 하나의 파티션에 저장됩니다.  

이로 인해 해당 도시의 데이터가 너무 많이 집중되어 부하가 발생할 수 있습니다.  

또한 "CustomerID"를 정렬 키로 사용하면 파티션 내에서 고객 ID별로 데이터가 정렬되지만, 파티션 간에는 정렬되지 않습니다.  

이러한 경우 쿼리 성능이 저하될 수 있습니다.

따라서 파티셔닝을 설계할 때는 데이터의 분산과 쿼리 성능을 고려하여 적절한 파티션 키와 정렬 키를 선택해야 합니다.