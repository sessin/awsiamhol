+++
title = "실습 안내"
weight = 1
pre = "<b>1.1 </b>"
+++
* * *
본 실습에서는 IAM(Identity and Access Management) 서비스를 통하여 사용자, 그룹, 역할을 생성하고 각 IAM 구성 요소에 해당하는 권한을 할당하여 관리자가 원하는 AWS 이용 환경에 대한 권한 관리를 어떻게 효율적으로 할 수 있는지에 대하여 알아 봅니다.


본 실습은 아래의 내용을 포함하고 있습니다.
•	IAM 사용자, 그룹, 역할 생성
•	IAM 내의 항목 및 요소들의 의미
•	Permission Boundary 의 이해
•	IAM 의 권할 할당 원리 및 과정
•	IAM Policy 구성 요소의 이해 및 생성

참고 1 : Lab Guide에 삽입된 Screenshot 들은 Lab 수행을 돕기 위하여 작성되었습니다. Lab 수행 중 생성하는 각각의 요소들의 식별자(ID)는 사용자 계정마다 다르다는 것을 인지 하시기 바랍니다.

참고 2 : 서울 리전(Region)을 선택하여 진행하기 바랍니다.

참고 3 : 실습 중 다양한 기능의 빠른 사용을 위하여 자주 사용하는 서비스를 사용하기 쉽도록 상단 메뉴바에 배치할 수 있습니다. 화면 상단의 Pin 아이콘을 선택하고, 자주 사용하는 서비스를 끌어 메뉴 상단에 배치하십시오. 

본 실습은 한국어 AWS 관리 콘솔을 기준으로 작성되었습니다. 관리 콘솔 하단의 언어 선택 메뉴를 통하여 원하는 언어로 전환할 수 있습니다.


* * *
### 실습을 통해 생성되는 AWS 자원
| AWS 서비스 유형| 리소스명	| 기타 |
|-------------|--------|-----|
|EC2 인스턴스	 |WAFLab-WebServerInstance	| t2.micro|
|ALB|	MyDVW-Applica…|	-|
|VPC|	VPC|	10.10.0.0/16|
|VPC Subnet|	PublicSubnet	|10.10.0.0/18|
|VPC Subnet|	PrivateSubnet	|10.10.64.0/18|
|WAF WebACLs|	WAFRule	|-
|기타 서비스|	Elastic IP, Route table, Security Groups, Network ACL, IAM Role 등|


* * *

사전 준비 단계에서 사용되는 CloudFormation 에서는 아래와 같은 AWS 리소스를 생성하여 실습 환경을 구성합니다.
![Lab Diagram](/images/waflab_diagram.png)