+++
title = "권한 경계(Permission Boudnardy)의 사용"
weight = 2
pre = "<b>3.2 </b>"
+++

* * *
### IAM 정책을 이용한 권한 제한 확인 – ec2_admin 사용자의 서울 리전 제한  
이 과정에서는 위 과정에서 만들었던 IAM 사용자의 권한을 IAM 의 정책 중 하나인 “권한 경계(Permission Boundary)” 기능을 이용하여 제한하는 방법을 수행하도록 하겠습니다.  “권한 경계” 는 일반적인 정책과 함께 IAM 사용자 혹은 IAM 역할에 할당되어 해당 IAM 주체의 권한을 제한하는 기능을 제공합니다. IAM 사용자나 역할에 “권한 경계” 와 정책이 함께 할당되게 되면 해당 IAM 사용자나 역할은 “권한 경계” 와 정책에 모두 포함되어 있는 권한(교집합의 개념)만 수행할 수 있게 됩니다.
 IAM 의 설정을 변경하기 위하여 아래와 같이 "super_admin” 사용자를 이용하여 Management Console 에 로그인합니다.
            

1. IAM 설정 변경을 위하여 IAM 메뉴로 이동합니다.
![Verification](/images/iam_menu.png)
2. “권한 경계” 설정을 추가하기 위해서 IAM 메뉴 중 “사용자” 를 선택한 후 “ec2_admin” 을 클릭합니다.
![Verification](/images/iam_selectadmin.png)
3. “ec2_admin” 의 상세 메뉴 화면 중 “권한” 탭의 하단에 있는 “경계 설정” 메뉴를 클릭합니다.
![Verification](/images/iam_selectpb.png)         
4. “권한 경계” 로 사용할 정책을 설정하기 위하여 “정책 필터” 에서 이전 과정에서 생성하였던 정책을 검색합니다. 검색어로 “deny-all” 을 입력하면 아래와 같이 이전 과정에서 생성하였던 “deny-all-out-side-of-seoul” 정책이 나타나는 것을 볼 수 있습니다. 이 정책을 사용하기 위하여 아래와 같이 라디오 버튼을 선택한 후 “경계 설정” 버튼을 클릭합니다.
![Verification](/images/iam_addpolicy_pb.png)
아래와 같이 “권한 경계” 가 “deny-all-out-side-of-seoul” 정책을 통해 설정되었음을 확인할 수 있습니다.
![Verification](/images/iam_view_pb.png)
5. 이번에는 “권한 경계” 가 적용된 “ec2_admin” 의 권한이 어떻게 바뀌었는지 확인하기 위하여 Management Console 을 로그아웃한 후 “ec2_admin” 사용자로 로그인을 합니다.
![Verification](/images/my_ec2admin_login.png)  
6. 화면 우측 상단의 메뉴를 클릭하여 아래와 같이 “서울 리전” 이 아닌 “싱가포르 리전” 을 선택합니다.
{{% notice info %}}
 * “싱가포르 리전” 이 아닌 다른 리전을 선택하더라도 결과는 동일합니다.
 {{% /notice %}}
![Verification](/images/select_region.png)
7. “싱가포르 리전” 에서의 “ec2_admin” 사용자의 EC2 관련 권한을 확인하기 위하여 Management Console 에서 EC2 메뉴로 이동합니다.
![Verification](/images/ec2_menu.png)
8. 정상적으로 “권한 경계” 가 설정되었다면 아래와 같이 “ec2_admin” 사용자가 “서울 리전” 이 아닌 다른 리전에서는 아래와 같이 EC2 관련 권한이 사라진 것을 확인할 수 있습니다.
![Verification](/images/sg_no_permission.png)