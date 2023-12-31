### Global Table
Global Table이란 DynamoDB의 기능 중 하나로 글로벌하게 분산된 다중 지역에 걸친 데이터베이스를 제공하는 서비스 입니다.  

Global Table을 사용하여 전 세계 여러 지역에 DynamoDB 테이블을 복제하고 동기화하여 전역 사용자에게 빠르고 일관된 읽기 및 쓰기 액세스를 제공할 수 있게 됩니다.  

Global Table의 특징
1. 다중 지역 복제  


Global Table은 여러 AWS 리전에 걸쳐 DynamoDB 테이블을 자동으로 복제합니다.  

이렇게 하면 데이터를 여러 지역에 배포하여 지리적으로 가까운 사용자에게 낮은 지연 시간과 높은 가용성을 제공합니다.

2. 동기화  

Global Table은 자동으로 지역 간 데이터를 동기화하여 데이터의 일관성을 보장합니다.  

데이터가 한 지역에서 변경되면 해당 변경 사항이 다른 지역의 테이블로 복제되어 동일한 데이터를 유지합니다.

3. 비동기적 복제  

쓰기 요청은 기본적으로 테이블이 속한 지역에서 수행되며, 해당 지역의 테이블은 비동기적으로 다른 지역으로 복제됩니다.  

이로 인해 쓰기 지연이 발생할 수 있지만 읽기 지연은 최소화됩니다.

4. 읽기 및 쓰기 우선순위  

Global Table은 여러 지역에 있는 테이블 간에 읽기 및 쓰기 우선순위를 설정할 수 있습니다.  

각 테이블은 자체적으로 우선순위를 설정하며, 우선순위가 높은 테이블이 우선적으로 쓰기 작업을 수행합니다.

5. 지역 간 데이터 정합성  

Global Table은 Multi-Master Replication을 지원하여 여러 지역에서 동시에 쓰기를 수행할 수 있습니다.

이는 지역 간에 충돌이 발생할 수 있는 가능성을 의미합니다.  

DynamoDB는 Conflict Resolution 기능을 제공하여 이러한 충돌을 해결할 수 있습니다.