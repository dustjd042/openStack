<img width="907" height="52" alt="image" src="https://github.com/user-attachments/assets/80967e0e-22c6-461c-bf5d-c4064d5c2841" /><img width="691" height="52" alt="image" src="https://github.com/user-attachments/assets/f4d532a8-79d1-4201-9711-c9ae5b42febf" />




# [OpenStack을 이용한 클라우드 시스템 구축] (4) 환경구성 1
### OpenStack 구축 방법
1. Installation: 가장 기본적인 수동적인 구축 방법 (해당 수업 실습 방법)
2. DevStack: 개발 환경 구성 신속하게 1회성 구축을 위한 방법
3. Deployment: 운영 환경 구성을 위한 구축 방법 (자동 배포 도구를 활용)

### 설치
* [virtualbox](https://www.virtualbox.org/wiki/Downloads)
* [ubuntu](https://releases.ubuntu.com)

### 접속
* ssh -p 10001 ubuntu@192.168.0.25
* ssh -p 10003 ubuntu@192.168.0.25

# 설치 버전
antelope

* MySQL
mysql -u root -p
SELECT user, host FROM mysql.user;
CREATE USER 'root'@'%' IDENTIFIED BY '비밀번호';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' WITH GRANT OPTION;
FLUSH PRIVILEGES;

* 레딧MQ 모니터링
sudo rabbitmq-plugins enable rabbitmq_management
sudo rabbitmqctl set_user_tags openstack administrator
http://192.168.0.25:15672/#/

* Memcached

* etcd
신뢰 가능한 상태 저장소
etcd = OpenStack의 “분산 상태/결정의 기준점 (source of truth)”
etcd는 “여러 서버가 동시에 같은 사실을 인정하게 만드는 방식(합의)”이 내장돼 있다
Raft 합의 알고리즘

* 인프라 모니터링
systemctl status --all
systemctl list-units --failed

* keystone
인증 서비스, 역할 권한 제어
https://docs.openstack.org/keystone/2023.1/install/

* Glance
https://docs.openstack.org/glance/2023.1/install/
VM 이미지(디스크 이미지) 저장, 검색, 배포
/var/lib/glance/images/.: 이미지 저장 장소

* Placement
https://docs.openstack.org/placement/2023.1/install/
클라우드 자원의 효율적 할당 및 관리 최적화를 위한 서비스

* Nova
가상 머심(VM) 인스턴스를 생성, 관리, 배포하는 컴퓨팅 자원 관리 서비스
직접 인스턴스를 생성 관리 수정하는 것이 아닌 컴퓨트 노드 KVM에 관련 요청을 보낸다.
(https://docs.openstack.org/nova/2023.1/install/)

* Neutron
네트워크 연결을 관리하고, 가상 네트워크, 서브넷, 라우터 등을 구성하는 서비스
https://docs.openstack.org/neutron/2023.1/install/
OVS : https://docs.openstack.org/neutron/2023.1/admin/deploy-ovs-selfservice.html

* Horizon
OpenStack의 모든 서비스를 웹 기반 GUI로 관리할 수 있게 해주는 대시보드 서비스
패키지 설치 방법과 소스코드 수동 설치 방법이 존재
https://docs.openstack.org/horizon/2023.1/install/

---
> 본 콘텐츠는 과학기술정보통신부 및 정보통신기획평가원의 「SW중심대학사업」 지원을 받아 제작된 자료를 기반으로 작성되었습니다.
* [OpenStack을 이용한 클라우드 시스템 구축](https://www.youtube.com/watch?v=X_5eMWyeH3Q&list=PLpiZz61rRNHXfCQC2-wfINlW9iO2PeOT7&index=2)
  
> 본 콘텐츠는 「CC BY-NC-SA」 라이선스를 따르는 자료를 참고하여 작성되었습니다.
* [OpenStackPractice](https://github.com/JBNU-JEduTools/OpenStackPractice)
