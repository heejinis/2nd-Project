# AWS EKS를 활용한 3-Tier 웹 서비스 구축

## 📑목차
- [프로젝트 소개](#-프로젝트-소개) 
- [핵심 기술](#-핵심-기술)  
- [기술 스택](#-기술-스택)  
- [아키텍처](#-아키텍처)  
- [PAGE](#-page)  
- [테스트 영상](#-테스트-영상)  
- [산출물](#-산출물)

## 🖥️ 프로젝트 소개

본 프로젝트는 **AWS EKS를 활용해 3-Tier 아키텍처** 기반의 웹 서비스를 구축하는 것을 목표로 합니다. 

고객이 자가 서비스로 주문하고 결제할 수 있는 온라인 플랫폼을 제공하여 대기 시간을 최소화하고 사용자 경험을 향상시킵니다. 

EKS 기반 클라우드 인프라 설계: AWS의 관리형 서비스인 **EKS**를 활용하여 안정적이고 손쉬운 클라우드 인프라를 구축했습니다. Cluster Autoscaler(CA)와 Horizontal Pod Autoscaler(HPA)를 적용해 고가용성을 보장하고, JMeter 부하 테스트로 시스템 성능을 검증했습니다. 또한, 이중화된 Application Load Balancer(ALB)를 구성하여 예상치 못한 상황에서도 안정적인 서비스를 유지할 수 있도록 설계했습니다.

데이터 관리 및 성능 최적화: **EFS(Elastic File System)** 를 도입해 확장 가능한 파일 관리 환경을 구축하고, **Redis**를 활용하여 Tomcat 세션 클러스터링과 고성능 인메모리 데이터 처리를 구현했습니다. 또한, **RDS와 Redis의 이중화 설정**을 통해 데이터베이스의 안정성 및 내구성을 강화했습니다.

자동화된 배포 및 업데이트: **ArgoCD와 GitHub를 연동한 CD(Continuous Deployment) 파이프라인**을 통해 서비스 할인 이벤트 및 상품 정보 변경 시 자동 업데이트를 구현했습니다. 코드 변경 사항은 신속하게 배포되며, 롤링 업데이트와 롤백 기능을 통해 서비스 안정성을 더욱 강화했습니다.

이러한 시스템 설계를 통해 서비스의 안정성과 효율성을 극대화하고, 고객 만족도를 향상시킬 수 있는 기반을 마련했습니다.


## 🚀 핵심 기술
| Technology            | Description          |
|-----------------------|---------------------------------------------------------------------------------------------------|
| **고가용성HA**         | CA, HPA, EFS, Multi-AZ, Read Replica, ALB 이중화 등을 활용하여 장애 발생 시에도 서비스가 정상적으로 운영되도록 고가용성을 유지했습니다. |
| **EFS(Elastic File System)**      | EFS를 사용하여 고가용성과 내구성을 보장했습니다. 데이터 손실이나 장애 발생 시에도 안정적인 데이터 접근을 제공하며, 다수의 인스턴스 간에 데이터를 공유할 수 있습니다. |
| **Redis**    | 메모리 기반의 Redis를 활용하여 빠른 데이터 접근을 가능하게 했습니다. 또한, 사용자 세션 데이터를 Redis에 저장하여 여러 서버 간에 세션을 공유하고 빠르게 읽고 쓸 수 있게 했습니다. |
| **배포 자동화 시스템** | GitHub를 사용하여 코드 관리 및 버전 관리를 자동화하고, ArgoCD를 활용해 Kubernetes 클러스터에 신속하고 안정적인 배포를 지원하는 시스템을 구축합니다. |
| **모니터링** | CloudWatch와 WhaTap을 연동하여 클러스터 상태를 모니터링하고, 장애 발생 시 실시간 경보 알림을 통해 빠르게 대응할 수 있도록 설정했습니다. |



## 🛠 기술 스택

<table>
<tr>
 <td align="center">프로그래밍 언어</td>
 <td>
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=JavaScript&logoColor=ffffff"/> <!--Java Script-->  
  <img src="https://img.shields.io/badge/Java-orange?style=for-the-badge&logo=Java&logoColor=white"/> <!--Java-->  
  <img src="https://img.shields.io/badge/html5-E34F26?style=for-the-badge&logo=html5&logoColor=white"/> <!--Html-->   
  <img src="https://img.shields.io/badge/css-1572B6?style=for-the-badge&logo=css3&logoColor=white"/> <!--Css-->  
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=MySQL&logoColor=white"/> <!--Sql-->  
 </td>
</tr>

<tr>
 <td align="center">프레임워크</td>
 <td>
  <img src="https://img.shields.io/badge/JSP-FF5F00?style=for-the-badge&logo=Java&logoColor=white"/> <!--Jsp-->  
  <img src="https://img.shields.io/badge/Spring-6DB33F?style=for-the-badge&logo=Spring&logoColor=ffffff"/> <!--Spring-->  
 </td>
</tr>

<tr>
 <td align="center">인프라</td>
 <td>
  <img src="https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white"/> <!--AWS-->  
  <img src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=Kubernetes&logoColor=white"/> <!--Kubernetes-->  
  <img src="https://img.shields.io/badge/amazoneks-000000?style=for-the-badge&logo=amazoneks53&logoColor=#FF9900"/> <!--EKS-->
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=Ubuntu&logoColor=white"/> <!--Ubuntu-->   
  <img src="https://img.shields.io/badge/docker-2496ED?style=for-the-badge&logo=docker&logoColor=ffffff"/> <!--Docker-->
  <img src="https://img.shields.io/badge/nginx-009639?style=for-the-badge&logo=nginx&logoColor=white"/> <!--Nginx-->
  <img src="https://img.shields.io/badge/tomcat-F8DC75?style=for-the-badge&logo=apachetomcat&logoColor=black"/> <!--Tomcat--> 
  <img src="https://img.shields.io/badge/amazonrds-000000?style=for-the-badge&logo=amazonrds&logoColor=#527FFF"/> <!--RDS-->  
  <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=Redis&logoColor=white"/> <!--Redis-->  
  <img src="https://img.shields.io/badge/Amazon%20EC2-FF9900?style=for-the-badge&logo=Amazon%20EC2&logoColor=white"/> <!--EC2-->
  <img src="https://img.shields.io/badge/EFS-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white" alt="EFS"/> <!--EFS-->
  <img src="https://img.shields.io/badge/Amazon_ECR-FF4F00?style=for-the-badge&logo=amazon-aws&logoColor=white" alt="ECR"/> <!--ECR-->
  <img src="https://img.shields.io/badge/linux-FCC624?style=for-the-badge&logo=linux&logoColor=black"/> <!--Linux--> 
  <img src="https://img.shields.io/badge/MariaDB-003545?style=for-the-badge&logo=mariadb&logoColor=white"/> <!--MariaDB-->
  <img src="https://img.shields.io/badge/amazonroute53-000000?style=for-the-badge&logo=amazonroute53&logoColor=#8C4FFF"/> <!--Route53-->
  <img src="https://img.shields.io/badge/AWS%20ALB-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white"/> <!--ALB-->
 </td>
</tr>

<tr>
 <td align="center">협업툴</td>
 <td>
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=Git&logoColor=white"/> <!--Git-->  
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=GitHub&logoColor=white"/> <!--GitHub-->
  <img src="https://img.shields.io/badge/GitHub Actions-2088FF?style=for-the-badge&logo=GitHub Actions&logoColor=white"/> <!--GitHub Action-->
  <img src="https://img.shields.io/badge/ArgoCD-3C7C7B?style=for-the-badge&logo=argo&logoColor=white"/> <!--ArgoCD-->
 </td>
</tr>

<tr>
 <td align="center">기타</td>
 <td>
  <img src="https://img.shields.io/badge/WhaTap-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhaTap"/> <!--WhaTap--> 
  <img src="https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=Notion&logoColor=white"/> <!--Notion-->  
  <img src="https://img.shields.io/badge/JSON-000000?style=for-the-badge&logo=json&logoColor=white"/> <!--Json-->  
 </td>
</tr>
</table>



## 🧱 아키텍처
![전체시방서](https://github.com/user-attachments/assets/b6f4a4f6-f797-48b7-b419-83845250e439)



## 🌐 PAGE
* 메인
![main](https://github.com/user-attachments/assets/41530446-b8ca-4fb6-b6bc-3038d6512a2f)

* 회원가입
![signup](https://github.com/user-attachments/assets/ce054152-13a2-4f7e-891c-fde07e78db7d)

* 주문
![order1](https://github.com/user-attachments/assets/4f106635-388f-484b-9d16-2bd7ba2ac31b)
![order2](https://github.com/user-attachments/assets/8d061288-8323-47f8-b7dd-e3991c8deefe)



## 🧪 테스트 영상
* Redis 적용

![Redis](https://github.com/user-attachments/assets/0c208672-ed6f-42fb-8035-d61ee19ca68d)

* 부하테스트 Whatap 모니터링

![부하테스트 및 Whatap 모니터링](https://github.com/user-attachments/assets/ac0c83a1-62e9-4c79-960f-788232de985f)


## 📦 산출물
JSP는 용량문제로 코드만 첨부합니다.

PPT는 용량문제로 분할 첨부합니다.

* Dockerfile
* yaml
* JSP
* WBS
* 관리대장
* 기술보고서
* PPT
