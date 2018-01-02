---

copyright:
  years: 2016, 2017
lastupdated: "2017-12-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 開始使用 GitHub Enterprise on IBM Cloud
{: #gheded_getting_started}

GitHub Enterprise on IBM Cloud 是 IBM Cloud 管理且完整管理的 {{site.data.keyword.ghe_short}} 版本，可供「專用 {{site.data.keyword.Bluemix_notm}}」環境使用。GitHub 提供開發人員喜愛的社交編碼體驗。[「{{site.data.keyword.Bluemix_notm}} 專用」![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/dedicated/index.html#dedicated){: new_window} 可在整合至網路的實體隔離硬體上提供雲端運算環境。

「專用 {{site.data.keyword.ghe_short}}」僅適用於「{{site.data.keyword.Bluemix_notm}} 專用」客戶。

{: #ghe_setaccount}
## 設定您的帳戶

{{site.data.keyword.ghe_short}} 包括搭配「{{site.data.keyword.Bluemix_notm}} 專用」的單一登入。若要登入 {{site.data.keyword.ghe_short}}，請將來自地區管理者或歡迎使用電子郵件的 URL 貼入瀏覽器中。 URL 將遵循此型樣：`github.your-company-dedicated-name.bluemix.net`。使用您的「{{site.data.keyword.Bluemix_notm}} 專用」使用者 ID 及密碼進行登入。您的 {{site.data.keyword.ghe_short}} 帳戶是自動建立的。

**附註：**如果訊息陳述您的使用者 ID 不存在，請要求地區管理者，將您的使用者 ID 新增至「{{site.data.keyword.Bluemix_notm}} 專用」使用者登錄。如果您是地區管理者，請參閱[管理「{{site.data.keyword.Bluemix_notm}} 專用」使用者及許可權 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/admin/index.html#oc_useradmin){: new_window}。

在大部分情況下，您的 GitHub 使用者名稱即是您的電子郵件簡稱，除非您的簡稱包括 GitHub 不支援的字元，例如句點。如果您的簡稱包括 GitHub 不支援的字元，則破折號會取代這些字元。     

{: #ghe_email}
## 將電子郵件位址新增至您的帳戶

若要接收通知，您必須將電子郵件位址新增 {{site.data.keyword.ghe_short}} 帳戶設定。在新增電子郵件位址之後，您可以利用 {{site.data.keyword.ghe_short}} 的社交編碼功能。    

若要將電子郵件位址新增至「專用 {{site.data.keyword.ghe_short}}」帳戶，請遵循下列步驟：    
1. 在任何 GitHub 頁面上，按一下您的設定檔圖示，然後按一下**設定**。    
2. 在資訊看板上，按一下**電子郵件**。    
3. 新增電子郵件位址，然後按一下**新增**。        

{: #ghe_auth}
## 建立個人存取記號或 SSH 金鑰進行鑑別

若要從本端 Git 儲存庫執行遠端 Git 作業，例如 `clone` 或 `push`，您必須使用個人存取記號或 SSH 金鑰，利用 {{site.data.keyword.ghe_short}} 進行鑑別。僅使用存取記號時，才支援透過 HTTPS 進行鑑別；您無法使用您的使用者 ID 及密碼，從本端儲存庫進行複製或推送。API 要求也需要個人存取記號。

**附註：**若要使用個人存取記號或 SSH 金鑰進行鑑別，您必須在本端設定 Git。如需指示，請參閱[設定 Git ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://help.github.com/enterprise/user/articles/set-up-git/){: new_window}。    

若要建立個人存取記號，請遵循下列步驟：    
   1. 在任何 GitHub 頁面上，按一下您的設定檔圖示，然後按一下**設定**。    
   2. 在資訊看板上，按一下**個人存取記號**。   
   3. 按一下**產生新記號**。
   4. 新增記號說明，然後按一下**產生記號**。
   5. 將記號複製到安全位置或密碼管理應用程式。    
     **附註：**基於安全原因，在您離開頁面之後，再也看不到記號。    

使用您的個人存取記號而非密碼，透過 HTTPS 存取指令行。


若要建立 SSH 金鑰，請遵循下列步驟：
   1. 開啟 Git Bash (Windows) 或新的「終端機」視窗（Linux 及 Mac）。    
   2. 貼上下列文字，並替換為您已新增至 {{site.data.keyword.ghe_short}} 帳戶的電子郵件位址：

     ````
     ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
     # Creates a new ssh key, using the provided email as a label
     Generating public/private rsa key pair.
     ````

   3. 當提示您指定要在其中儲存金鑰的檔案時，請按 Enter 來接受預設位置。
   4. 在提示中，鍵入安全通行詞組。如需相關資訊，請參閱[使用 SSH 金鑰通行詞組 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://help.github.com/enterprise/user/articles/working-with-ssh-key-passphrases/){: new_window}。   

將 SSH 金鑰新增至 ssh-agent：    
   1. 確定 ssh-agent 已啟用。請使用 Git Bash 來輸入此指令，以啟用 ssh-agent：
      ````
      # start the ssh-agent in the background
      $ eval "$(ssh-agent -s)"
      Agent pid 59566
      ````    

   2. 輸入下列指令，將您的 SSH 金鑰新增至 ssh-agent：    
      ````
      $ ssh-add ~/.ssh/id_rsa
      ````    
   3. 將 SSH 金鑰新增至您的 GitHub 帳戶。如需相關資訊，請參閱[新增 SSH 金鑰至 GitHub 帳戶 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://help.github.com/enterprise/user/articles/adding-a-new-ssh-key-to-your-github-account/){: new_window}。    


{: #ghe_orgs}
## 設定 GitHub 組織、團隊及儲存庫    

設定 GitHub 組織很有用，因為您可以建立相異的使用者群組，使用類似的專案或作業。組織內的組織團隊具有可以控制儲存庫存取的附加好處。如需相關資訊，請參閱[組織與團隊 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://help.github.com/enterprise/admin/guides/user-management/organizations-and-teams/){: new_window}。

**附註：**GitHub 組織與 {{site.data.keyword.Bluemix_notm}} 組織不相同。

完成下列作業來設定團隊專案：

   1. [建立組織 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://help.github.com/enterprise/user/articles/creating-a-new-organization-account/){: new_window}。
   2. [建立組織的儲存庫 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://help.github.com/enterprise/user/articles/create-a-repo/){: new_window}。
   3. [邀請使用者加入組織 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://help.github.com/articles/inviting-users-to-join-your-organization/){: new_window}。

  **附註：**在您邀請使用者加入組織之前，他們必須登入 {{site.data.keyword.ghe_short}} 至少一次，否則將無法邀請其 {{site.data.keyword.ghe_short}} 帳戶。

<!-- ### Getting support
To get answers now, submit questions to [Stack Overflow ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://stackoverflow.com/questions/ask?tags=ibm-bluemix_github-enterprise){: new_window}.

For more support, use these resources:    
   1. Complete the form at 
   [IBM Cloud Support Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/bluemixsupport) 
   2. Submit a new ticket through the 
   [Client Success Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](
   https://support.ibmcloud.com/ics/support/mylogin.asp?login=bluemix). -->
