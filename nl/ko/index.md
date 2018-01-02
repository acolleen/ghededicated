---

copyright:
  years: 2016, 2017
lastupdated: "2017-12-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# GitHub Enterprise on IBM Cloud 시작하기
{: #gheded_getting_started}

GitHub Enterprise on IBM Cloud는 IBM Cloud에서 호스팅하고 완전하게 관리되는 {{site.data.keyword.ghe_short}} 버전이며 Dedicated {{site.data.keyword.Bluemix_notm}} 환경에서 사용할 수 있습니다. GitHub에서는 개발자가 좋아하는 특수 코딩 환경을 제공합니다. [{{site.data.keyword.Bluemix_notm}} Dedicated ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/dedicated/index.html#dedicated){: new_window}에서는 네트워크에 통합되어 있는 물리적으로 격리된 하드웨어에서 클라우드 컴퓨팅 환경을 제공합니다.

Dedicated {{site.data.keyword.ghe_short}}는 {{site.data.keyword.Bluemix_notm}} Dedicated 고객 전용입니다.

{: #ghe_setaccount}
## 계정 설정

{{site.data.keyword.ghe_short}}에는 {{site.data.keyword.Bluemix_notm}} Dedicated를 사용한 싱글 사인온이 포함되어 있습니다. {{site.data.keyword.ghe_short}}에 로그인하려면 지역 관리자나 환영 이메일의 URL을 브라우저에 붙여넣으십시오. URL은 `github.your-company-dedicated-name.bluemix.net` 패턴을 따릅니다. {{site.data.keyword.Bluemix_notm}} Dedicated 사용자 ID와 비밀번호를 사용하여 로그인하십시오. {{site.data.keyword.ghe_short}} 계정이 자동으로 작성됩니다. 

**참고:** 사용자 ID가 존재하지 않는다는 메시지가 표시되면 지역 관리자에게 사용자 ID를 {{site.data.keyword.Bluemix_notm}} Dedicated 사용자 레지스트리에 추가하도록 요청하십시오. 지역 관리자인 경우 [{{site.data.keyword.Bluemix_notm}} Dedicated 사용자 및 권한 관리 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/admin/index.html#oc_useradmin){: new_window}를 참조하십시오.

대부분의 경우 GitHub 사용자 이름은 짧은 이메일 이름입니다. 단, 짧은 이름에 GitHub에서 지원하지 않는 문자(예: 마침표(.))가 포함된 경우는 예외입니다. 짧은 이름에 GitHub에서 지원하지 않는 문자를 포함하면 문자를 대시로 바꿉니다.     

{: #ghe_email}
## 이메일 주소를 계정에 추가

알림을 받으려면 {{site.data.keyword.ghe_short}} 계정 설정에 이메일 주소를 추가해야 합니다. 이메일 주소를 추가하고 나면 {{site.data.keyword.ghe_short}}의 특수 코딩 기능을 이용할 수 있습니다.    

Dedicated {{site.data.keyword.ghe_short}} 계정에 이메일 주소를 추가하려면 다음 단계를 따르십시오.    
1. 모든 GitHub 페이지에서 프로파일 아이콘을 클릭한 다음 **설정**을 클릭하십시오.    
2. 사이드바에서 **이메일**을 클릭하십시오.    
3. 이메일 주소를 추가하고 **추가**를 클릭하십시오.        

{: #ghe_auth}
## 인증용 개인 액세스 토큰 또는 SSH 키 작성

로컬 Git 저장소에서 원격 Git 오퍼레이션(예: `clone` 또는 `push`)을 수행하려면 개인 액세스 토큰 또는 SSH 키를 사용하여 {{site.data.keyword.ghe_short}}를 인증해야 합니다. HTTPS를 통한 인증은 액세스 토큰만 사용하여 지원됩니다. 사용자 ID와 비밀번호를 사용하여 로컬 저장소에서 복제하거나 푸시할 수 없습니다. API 요청에는 개인 액세스 토큰도 필요합니다.

**참고:** 인증에 개인 액세스 토큰 또는 SSH 키를 사용하려면 로컬에서 Git를 설정해야 합니다. 지시사항은 [Git 설정 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://help.github.com/enterprise/user/articles/set-up-git/){: new_window}을 참조하십시오.    

개인 액세스 토큰을 작성하려면 다음 단계를 따르십시오.    
   1. 모든 GitHub 페이지에서 프로파일 아이콘을 클릭한 다음 **설정**을 클릭하십시오.    
   2. 사이드바에서 **개인 액세스 토큰**을 클릭하십시오.   
   3. **새 토큰 생성**을 클릭하십시오.
   4. 토큰 설명을 추가하고 **토큰 생성**을 클릭하십시오.
   5. 안전한 위치 또는 비밀번호 관리 앱에 토큰을 복사하십시오.    
     **참고:** 보안상의 이유로 인해 페이지를 종료하고 나면 더 이상 토큰을 다시 볼 수 없습니다.    

HTTPS를 통해 명령행에 액세스하는 데 비밀번호가 아니라 개인 액세스 토큰을 사용하십시오.


SSH 키를 작성하려면 다음 단계를 따르십시오.
   1. Git Bash(Windows) 또는 새 터미널 창(Linux 및 Mac)을 여십시오.    
   2. {{site.data.keyword.ghe_short}} 계정에 추가한 이메일 주소를 대체하여 다음 텍스트를 붙여넣으십시오.

     ````
     ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
     # Creates a new ssh key, using the provided email as a label
     Generating public/private rsa key pair.
     ````

   3. 키를 저장할 파일을 지정하도록 프롬프트가 표시되면 Enter를 눌러 기본 위치를 승인하십시오.
   4. 프롬프트에서 안전한 비밀번호 문구를 입력하십시오. 자세한 정보는 [SSH 키 비밀번호 문구에 대한 작업 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://help.github.com/enterprise/user/articles/working-with-ssh-key-passphrases/){: new_window}을 참조하십시오.   

다음과 같이 SSH 키를 ssh-agent에 추가하십시오.    
   1. ssh-agent가 사용되는지 확인하십시오. Git Bash에서 다음 명령을 입력하여 ssh-agent를 사용하도록 설정하십시오.
      ````
      # start the ssh-agent in the background
      $ eval "$(ssh-agent -s)"
      Agent pid 59566
      ````    

   2. 다음 명령을 입력하여 SSH 키를 ssh-agent에 추가하십시오.    
      ````
      $ ssh-add ~/.ssh/id_rsa
      ````    
   3. SSH 키를 GitHub 계정에 추가하십시오. 자세한 정보는 [새 SSH 키를 GitHub 계정에 추가 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://help.github.com/enterprise/user/articles/adding-a-new-ssh-key-to-your-github-account/){: new_window}를 참조하십시오.    


{: #ghe_orgs}
## GitHub 조직, 팀 및 저장소 설정    

비슷한 프로젝트나 태스크에 대해 작업하는 개별 사용자 그룹을 작성하므로 GitHub 조직을 설정하면 유용합니다. 조직에서 팀을 구성하면 저장소에 대한 액세스를 제어하는 이점이 추가됩니다. 자세한 정보는 [조직 및 팀 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://help.github.com/enterprise/admin/guides/user-management/organizations-and-teams/){: new_window}을 참조하십시오.

**참고:** GitHub 조직은 {{site.data.keyword.Bluemix_notm}} 조직과 같지 않습니다.

다음 태스크를 완료하여 팀의 프로젝트를 설정하십시오.

   1. [조직(org) 작성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://help.github.com/enterprise/user/articles/creating-a-new-organization-account/){: new_window}.
   2. [조직의 저장소 작성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://help.github.com/enterprise/user/articles/create-a-repo/){: new_window}.
   3. [조직에 참여하도록 사용자 초대 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://help.github.com/articles/inviting-users-to-join-your-organization/){: new_window}.

  **참고:** 조직에 사용자를 초대하기 전에 {{site.data.keyword.ghe_short}}에 한 번 이상 로그인해야 합니다. 그렇지 않으면 {{site.data.keyword.ghe_short}} 계정을 초대할 수 없습니다.

<!-- ### Getting support
To get answers now, submit questions to [Stack Overflow ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://stackoverflow.com/questions/ask?tags=ibm-bluemix_github-enterprise){: new_window}.

For more support, use these resources:    
   1. Complete the form at 
   [IBM Cloud Support Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/bluemixsupport) 
   2. Submit a new ticket through the 
   [Client Success Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](
   https://support.ibmcloud.com/ics/support/mylogin.asp?login=bluemix). -->
