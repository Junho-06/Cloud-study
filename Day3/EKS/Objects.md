### k8s의 주요 Objects

쿠버네티스에서 오브젝트란 쿠버네티스를 구성하는 단위로, 가장 기본적인 구성단위인 기본 오브젝트 와 기본 오브젝트를 관리하고 추가적인 기능을 가진 컨트롤러로 이루어져 있습니다.  

### 기본 오브젝트
* Pod  

Pod는 쿠버네티스에서 컨테이너의 기본 단위로, 가장 기본적인 배포 단위 입니다.  

Pod는 1개 이상의 컨테이너로 구성된 컨테이너 집합이며, 아래는 Pod의 특징 입니다.  

    - 각 Pod에는 고유한 IP 주소가 할당됩니다.  
    - 같은 Pod내의 컨테이너는 IP와 Port 공간을 공유합니다.
    - 따라서 파드에 속한 컨테이너는 localhost를 사용하여 서로 통신할 수 있습니다.
    - Pod내의 컨테이너간에는 디스크 볼륨을 공유할 수 있습니다.

* Volume  

Pod가 생성될 때 컨테이너가 실행되면서 로컬 디스크를 생성하게 되는데, 이 로컬 디스크의 경우 컨테이너가 재실행되거나 종료되면 로컬 디스크 안에 있는 파일도 같이 손실된다는 단점이 있습니다.  

파일을 영구적으로 저장해야할 필요가 있다면 쿠버네티스는 이를 위해 영구적인 스토리지를 볼륨으로 제공합니다.  

볼륨은 Pod가 실행될 때 컨테이너에 마운트되어 사용되며 쉽게 컨테이너의 외장 디스크라고 생각하시면 됩니다.  

볼륨은 NFS, Cinder, CephFS 등과 같은 네트워크 스토리지부터 AWS EBS, Google PD, Azure Disk Storage 등과 같은 클라우드 스토리지까지 다양한 유형의 볼륨들을 지원하고 있습니다.  

유형에 따라 볼륨이 Pod 내부에 존재할 수도 있고 Pod 외부에 존재할 수도 있습니다.  

* Service  

클러스터 내부에서 실행되는 Pod들은 언제든지 삭제됬다가 생성될 수 있는 반 영속적인 특성을 지니고 있는데, Pod가 생성될 때마다 새로운 내부 IP를 할당하게 되므로, 클러스터 내/외부와 통신을 유지하기 어렵습니다.  

이를 위해서 쿠버네티스는 Service라는 기능을 제공합니다.  

이는 라벨링을 통해 같은 라벨을 가진 Pod를 묶어 단일 엔드포인트를 제공해주는 기능을 합니다.  

Service는 클러스터 내부에서 고정적인 IP를 갖고 있으며, Pod가 변경되어도 서비스의 IP는 변하지 않기 때문에 클러스터 내/외부와의 통신을 계속 유지할 수 있습니다.  

또한 Service는 Pod간의 로드밸런싱을 지원하고, 멀티 포트도 지원합니다.  

* 라벨  

라벨은 쿠버네티스의 리소스를 선택하는데 사용됩니다.  

모든 리소스는 라벨을 가질 수 있고, 라벨에 따라서 특정 라벨을 가지고 있는 리소스만 선택할 수도 있습니다.  

라벨로 선택된 리소스는 Service에 연결하거나 네트워크 접근 권한을 부여하는 등 다양하게 사용할 수 있습니다.  

라벨은 Key:Value 형태로 정의할 수 있으며, 하나의 리소스에 여러개의 라벨을 동시에 적용할 수도 있습니다.  

* Namespace  

Namespace는 쿠버네티스 클러스터 내의 리소스들을 논리적으로 구분할 수 있게 해주는 하나의 단위 입니다.  

Namespace는 논리적으로 구분하는거지 물리적으로 구분하는 것이 아니기 때문에 다른 Namespace간의 Pod라도 통신은 가능합니다.  

네트워크 정책을 통해 Namespace간의 통신을 막을 수 있지만 이럴 경우는 클러스터 자체를 분리시키는게 바람직합니다.  

### 컨트롤러
* ReplicationController  

ReplicationController(RC)는 Pod를 관리해주는 역할을 하는데, RC에 지정된 Replica 수보다 Pod가 많으면 Pod를 삭제하거나 Pod가 적으면 Pod를 추가하게 됩니다.  

사용자가 수동으로 생성한 Pod와 달리 RC가 관리하는 Pod의 경우 Pod가 삭제되거나 예기치 않게 종료되는 경우 Pod를 자동으로 교체합니다.  

RC는 크게 아래 3가지로 구성됩니다.

1. Selector
    * Selector는 라벨을 기반으로하며, 라벨을 지정하면 해당 라벨을 가진 모든 Pod를 관리합니다.
    * RC는 등호(Eqaulity)기반의 Selector를 사용합니다.
    * 따라서 라벨이 같은지(==) 다른지(!=)만 비교합니다.

2. Replica
    * RC에 의해 관리되는 Pod의 수 입니다.
    * Replica가 3이면 3개의 Pod만 띄우고, 만약 지정한 Replica보다 Pod의 수가 많다면 Pod를 삭제하고 적다면 Pod를 추가합니다.  

3. Template
    * 새로운 Pod를 추가할 때 해당 Pod에 대한 정보를 정의해야 하는데 이를 Template에 정의합니다.
    * 기존의 Pod가 Template에 정의된 스펙과 다를지라도 Replica 수에 맞게 Pod가 생성되어있다면 해당 Pod를 삭제하지 않습니다.

* ReplicaSet  

ReplicaSet은 RC의 상위 버전으로 ReplicaSet은 RC와 동일한 기능을 하지만 아래와 같은 차이점이 있습니다.  

1. Selector 
    * ReplicaSet은 집합 기반의 Selector를 사용합니다.
    * 따라서 In, notin, exists 같은 연산자를 지원합니다.

2. rolling-update
    * RC는 rolling-update 옵션을 사용할 수 있지만 ReplicaSet은 사용할 수 없습니다.
    * ReplicaSet은 Deployments를 통해 rolling-update를 사용할 수 있습니다.

* Deployment  

Deployment는 ReplicaSet의 상위개념으로, Pod와 ReplicaSet에 대한 배포를 관리합니다.  

운영 중에 어플리케이션의 새 버전을 배포 해야 하거나, 부하가 증가하면서 ReplicaSet을 추가하는 등 여러 가지 동작을 Deployment로 관리할 수 있습니다.  

Deployment는 배포에 대한 이력을 관리하는데 만약 배포한 새버전에 문제가 생긴경우 Deployment를 통해 쉽게 롤백이 가능합니다.  

Deployment에서 자주 사용되는 배포 전략으로는 Rolling Update, Blue/Green, Canary 등이 있습니다.

* StatefulSet  

StatefulSet은 Pod의 상태를 유지하고 관리할 때 사용됩니다.  

Deployment를 통해 Pod를 삭제하고 생성하면 완전히 새로운 가상환경이 시작되는데, 이 경우 StatefulSet을 사용하여 Pod를 생성하면 Pod가 삭제되었다 새로 생성되어도 기존의 상태를 그대로 유지가 가능합니다.  

하지만 Pod가 삭제 되는 경우 Deployment에 비해 빠르게 작업을 수행할 수 없습니다, 그 이유는 StatefulSet은 Deployment처럼 Pod가 삭제되면 Pod안에 있는 정보를 전부 삭제하는 것이 아니라 상태를 유지하기 위해 Pod가 삭제되었을 때 해당 Pod의 정보를 다른 Pod에 분산하여 저장하게 되기 때문입니다.  

* DaemonSet  

DaemonSet은 Deployment와 유사하게 Pod를 생성하고 관리하지만, 전체 노드에서 항상 실행되어야 하는 특정 Pod를 실행할 때 사용합니다.  

DaemonSet이 관리하는 Pod는 기본적으로 모든 노드에 균등하게 생성되지만, 특정 노드에만 Pod가 하나씩 생성되도록 구성할 수도 있습니다.

* Job  

Job은 하나 이상의 Pod를 지정하고 지정된 수의 Pod를 실행합니다.  

Pod가 정상적으로 실행되지 않았을 경우 Job은 새로운 Pod를 새로 생성하고 실행합니다.  

Job은 주로 백업이나 배치 작업같은 한번만 실행되고 종료되는 성격의 작업에 사용됩니다.  

Job은 재실행 정책에 따라 Pod 생성 실패시 수행하는 작업이 달라집니다.  

* CronJob  

CronJob은 Job을 주기적으로 실행시킵니다.  

Linux의 crontab과 유사합니다.  

CronJob은 주로 특정 시간에 실행되거나 일정 주기마다 실행되야하는 작업에 사용됩니다.