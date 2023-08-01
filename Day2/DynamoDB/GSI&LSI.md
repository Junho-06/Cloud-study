DynamoDB는 사용한 만큼 비용을 지불합니다.  

이러한 이유로 가능한 적은 양의 데이터를 쿼리하는 것이 유리하게 됩니다.  

하나의 key만으로는 다양한 어플리케이션의 요구사항을 만족시키기 어렵기 때문에 DynamoDB를 이용할때는 대부분 secondary index를 생성해서 사용합니다. 

### Secondary Index
Secondary Index란 대체 key와 테이블의 다른 attribute들의 subset을 포함하는 데이터 구조 입니다.  

테이블과 마찬가지로 Index에 쿼리를 해서 데이터를 가져올 수 있습니다.  

secondary index는 primary key와 다르게 여러개를 만드는 것이 가능하며, 때문에 여러가지 쿼리 패턴을 사용할 수 있습니다.  

secondary index를 만들 때는 기본적으로 다음의 세가지가 필요합니다.  

1. Base Table
2. Altanative Key (Partition key + sort key)
3. project하거나 복제할 attribute

### secondary index의 종류
1. Global Secondary Index (GSI)  

pk와 sk가 base table의 key들과 달라도 됩니다.  

데이터가 base table과 다른 partition에 저장됩니다.  

base table과 따로 scale 됩니다.  

쿼리를 할 때 모든 partition에 대해서 하기 때문에 global이라고 부릅니다.  

20개 까지 생성이 가능합니다.  

2. Local Secondary Index (LSI)  

base table과 같은 partition key, 다른 sort key를 사용합니다.  

partition key에 해당하는 하나의 partition에 대해서만 쿼리하기 때문에 local이라고 부릅니다.  

5개 까지 생성이 가능합니다.  