---

copyright:
  years: 2016, 2017
lastupdated: "2017-12-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 开始使用 GitHub Enterprise on IBM Cloud
{: #gheded_getting_started}

GitHub Enterprise on IBM Cloud 是 IBM Cloud 托管且完全管理的 {{site.data.keyword.ghe_short}} 版本，适用于专用 {{site.data.keyword.Bluemix_notm}} 环境。GitHub 提供了开发者喜爱的社交编码体验。[{{site.data.keyword.Bluemix_notm}} Dedicated ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/dedicated/index.html#dedicated){: new_window} 提供了已集成到您网络的有关以物理方式隔离的硬件的云计算环境。

Dedicated {{site.data.keyword.ghe_short}} 仅适用于 {{site.data.keyword.Bluemix_notm}} Dedicated 客户。

{: #ghe_setaccount}
## 设置帐户

{{site.data.keyword.ghe_short}} 包含使用 {{site.data.keyword.Bluemix_notm}} Dedicated 进行单点登录。要登录到 {{site.data.keyword.ghe_short}}，请将区域管理员或者欢迎电子邮件中的 URL 粘贴到浏览器中。URL 应遵循以下模式：`github.your-company-dedicated-name.bluemix.net`。使用您的 {{site.data.keyword.Bluemix_notm}} Dedicated 用户标识和密码登录。将自动为您创建 {{site.data.keyword.ghe_short}} 帐户。

**注：** 如果消息指示您的用户标识不存在，那么请咨询区域管理员，将您的用户标识添加到 {{site.data.keyword.Bluemix_notm}} Dedicated 用户注册表中。如果您就是区域管理员，那么请参阅[管理 {{site.data.keyword.Bluemix_notm}} Dedicated 用户和许可权 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/admin/index.html#oc_useradmin){: new_window}。

在大多数情况下，GitHub 用户名就是您的电子邮件短名称，除非短名称中包含 GitHub 不支持的字符，例如句点。如果您的短名称中包含 GitHub 不支持的字符，那么这些字符将会被替换为连字符。     

{: #ghe_email}
## 将电子邮件地址添加到帐户

要想能接收到通知，必须将您的电子邮件地址添加到 {{site.data.keyword.ghe_short}} 帐户设置中。添加电子邮件地址后，您可以利用 {{site.data.keyword.ghe_short}} 的社交编码功能。    

要将电子邮件地址添加到 Dedicated {{site.data.keyword.ghe_short}} 帐户，请执行以下步骤：    
1. 在任何 GitHub 页面上，单击“概要文件”图标，然后单击**设置**。    
2. 在侧边栏上，单击**电子邮件**。    
3. 添加您的电子邮件地址，然后单击**添加**。        

{: #ghe_auth}
## 创建用于认证的个人访问令牌或 SSH 密钥

要执行远程 Git 操作，例如从本地 Git 存储库`克隆`或`推送`，您必须使用个人访问令牌或 SSH 密钥向 {{site.data.keyword.ghe_short}} 进行认证。通过 HTTPS 进行认证时，仅支持使用访问令牌。您无法通过用户标识和密码从本地存储库执行克隆或者推送操作。API 请求也需要个人访问令牌。

**注：**要使用个人访问令牌或 SSH 密钥进行认证，必须在本地设置 Git。有关指示信息，请参阅[设置 Git ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://help.github.com/enterprise/user/articles/set-up-git/){: new_window}。    

要创建个人访问令牌，请执行以下步骤：    
   1. 在任何 GitHub 页面上，单击“概要文件”图标，然后单击**设置**。    
   2. 在侧边栏上，单击**个人访问令牌**。   
   3. 单击**生成新令牌**。
   4. 添加令牌描述，然后单击**生成令牌**。
   5. 将令牌复制到安全位置或密码管理应用程序。    
     **注：**出于安全考虑，离开此页面后，将无法再看到该令牌。    

使用个人访问令牌而不是密码通过 HTTPS 来访问命令行。


要创建 SSH 密钥，请执行以下步骤：
   1. 打开 Git Bash ((Windows) 或新终端窗口 (Linux 和 Mac)。    
   2. 粘贴以下文本，替换已添加到 {{site.data.keyword.ghe_short}} 帐户的电子邮件地址：

     ````
     ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
     # Creates a new ssh key, using the provided email as a label
     Generating public/private rsa key pair.
     ````

   3. 当系统提示您指定保存密钥的某个文件时，请按 Enter 键接受该缺省位置。
   4. 在系统提示时，键入安全口令。有关更多信息，请参阅[使用 SSH 密钥口令![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://help.github.com/enterprise/user/articles/working-with-ssh-key-passphrases/){: new_window}。   

将 SSH 密钥添加到 ssh-agent：    
   1. 请确保 ssh-agent 已启用。通过使用 Git Bash，输入以下命令来启用 ssh-agent：
      ````
      # start the ssh-agent in the background
      $ eval "$(ssh-agent -s)"
      Agent pid 59566
      ````    

   2. 通过输入以下命令来将 SSH 密钥添加到 ssh-agent：    
      ````
      $ ssh-add ~/.ssh/id_rsa
      ````    
   3. 将 SSH 密钥 添加到 GitHub 帐户。有关更多信息，请参阅[将新 SSH 密钥添加到您的 GitHub 帐户![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://help.github.com/enterprise/user/articles/adding-a-new-ssh-key-to-your-github-account/){: new_window}。    


{: #ghe_orgs}
## 设置 GitHub 组织、团队和存储库    

设置 GitHub 组织非常有用，因为您创建了从事类似项目或任务的不同用户组。在组织内组织团队还具有控制对存储库访问权的额外好处。有关更多信息，请参阅[组织和团队![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://help.github.com/enterprise/admin/guides/user-management/organizations-and-teams/){: new_window}。

**注：**GitHub 组织与 {{site.data.keyword.Bluemix_notm}} 组织不同。

通过完成以下任务来设置团队的项目：

   1. [创建组织![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://help.github.com/enterprise/user/articles/creating-a-new-organization-account/){: new_window}。
   2. [为组织创建存储库![外部链接图标](../../icons/launch-glyph.svg "External link icon")](https://help.github.com/enterprise/user/articles/create-a-repo/){: new_window}。
   3. [邀请用户加入您的组织![外部链接图标](../../icons/launch-glyph.svg "External link icon")](https://help.github.com/articles/inviting-users-to-join-your-organization/){: new_window}。

  **注：**用户必须至少登录过一次 {{site.data.keyword.ghe_short}}，才能邀请他们加入您的组织，否者将不能对他们的 {{site.data.keyword.ghe_short}} 帐户发出邀请。

<!-- ### Getting support
To get answers now, submit questions to [Stack Overflow ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://stackoverflow.com/questions/ask?tags=ibm-bluemix_github-enterprise){: new_window}.

For more support, use these resources:    
   1. Complete the form at 
   [IBM Cloud Support Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/bluemixsupport) 
   2. Submit a new ticket through the 
   [Client Success Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](
   https://support.ibmcloud.com/ics/support/mylogin.asp?login=bluemix). -->
