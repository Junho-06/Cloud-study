### Cluster란
ECS의 가장 기본적인 단위로써 Cluster는 Task 또는 Service의 논리적인 그룹입니다.  

기본적으로 컴퓨팅 자원을 포함하지 않으며, ECS에서 컨테이너를 실행시키기 위해서는 Container Instance가 Cluster에 포함되어야 합니다.  

Cluster는 Container Instance를 조작할 수 있는 권한을 가지고 있으며, Cluster에서 Service나 Task를 실행하면 조건을 만족하는 Container Instance를 찾아 해당 Instance에 컨테이너를 실행합니다.  

AWS Fargate를 사용하면 Container Instance없이 컨테이너 실행이 가능합니다.  

### Service란
Service는 Task를 지속적으로 관리하는 단위 입니다.  

Service는 Cluster 내에서 지정된 Task 수만큼 동시에 실행하고 관리할 수 있습니다.  

또한 ELB와 연동하여 실행중인 Task를 찾아 자동으로 ELB에 등록 및 제거하는 Auto Scaling 역할도 담당합니다.  

### Task Definition
Task Defeinition은 Task를 실행시키기 위한 설정을 저장하고 있는 단위입니다.  

Task Definition은 컨테이너 별로 실행하고자 하는 이미지를 지정할 수 있으며, CPU나 Memory와 같은 정보도 지정할 수 있고, 하나 혹은 둘 이상의 Task Definition을 포함할 수 있습니다.  

Task Definition은 Cluster에 종속되어있지 않습니다.

### Task
Task는 ECS의 최소 실행 단위로 하나 이상의 컨테이너 묶음 입니다.  

Task를 실행하는 방법에는 Task Definition으로 직접 Task를 실행하는 방법과 Service를 정의하는 방법이 있습니다.  

Task Definition으로 직접 실행된 Task의 경우 처음 한 번 실행된 이후 관리되지 않습니다.  

Task는 Cluster에 속한 Container Instance에 배포됩니다.