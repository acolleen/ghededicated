---

copyright:
  years: 2016, 2017
lastupdated: "2017-12-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# GitHub Enterprise on IBM Cloud 概説
{: #gheded_getting_started}

GitHub Enterprise on IBM Cloud は、IBM Cloud でホストされて完全に管理されるバージョンの {{site.data.keyword.ghe_short}} で、専用 {{site.data.keyword.Bluemix_notm}} 環境に使用できます。GitHub は、開発者が希望するソーシャル・コーディング・エクスペリエンスを実現します。[{{site.data.keyword.Bluemix_notm}} Dedicated ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/dedicated/index.html#dedicated){: new_window} は、ネットワークに統合された、物理的に隔離されているハードウェア上にクラウド・コンピューティング環境を提供します。

専用 {{site.data.keyword.ghe_short}} は、{{site.data.keyword.Bluemix_notm}} Dedicated のお客様のみを対象としています。

{: #ghe_setaccount}
## アカウントのセットアップ

{{site.data.keyword.ghe_short}} には、{{site.data.keyword.Bluemix_notm}} Dedicated でのシングル・サインオンが含まれています。{{site.data.keyword.ghe_short}} にログインするには、地域管理者またはウェルカム E メールからの URL をブラウザーに貼り付けます。URL のパターンは、`github.your-company-dedicated-name.bluemix.net` のようになります。{{site.data.keyword.Bluemix_notm}} Dedicated ユーザー ID とパスワードを使用してサインインします。{{site.data.keyword.ghe_short}} アカウントが自動的に作成されます。

**注:** ユーザー ID が存在しないというメッセージが出される場合は、地域管理者にユーザー ID を {{site.data.keyword.Bluemix_notm}} Dedicated ユーザー・レジストリーに追加するように依頼してください。地域管理者は、[Managing {{site.data.keyword.Bluemix_notm}} Dedicated users and permissions ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/admin/index.html#oc_useradmin){: new_window} を参照してください。

ほとんどの場合、GitHub ユーザー名は E メールの短縮名です。ただし、短縮名に GitHub がサポートしない文字 (ピリオドなど) が含まれている場合を除きます。短縮名に GitHub がサポートしない文字が含まれている場合、その文字はダッシュに置き換えられます。     

{: #ghe_email}
## アカウントへの E メール・アドレスの追加

通知を受け取るには、{{site.data.keyword.ghe_short}} アカウントの設定に E メール・アドレスを追加する必要があります。E メール・アドレスを追加すると、{{site.data.keyword.ghe_short}} のソーシャル・コーディング機能を利用できるようになります。    

E メールを専用 {{site.data.keyword.ghe_short}} アカウントに追加するには、以下の手順に従います。    
1. 任意の GitHub ページで、プロファイル・アイコンをクリックして、**「設定」**をクリックします。    
2. サイドバーで、**「E メール」**をクリックします。    
3. E メール・アドレスを追加して、**「追加」**をクリックします。        

{: #ghe_auth}
## 認証のための個人用アクセス・トークンまたは SSH 鍵の作成

ローカル Git リポジトリーから `clone` や `push` などのリモート Git 操作を実行するには、個人用アクセス・トークンまたは SSH 鍵を使用して {{site.data.keyword.ghe_short}} で認証する必要があります。HTTPS 経由の認証では、アクセス・トークンの使用のみサポートされます。ユーザー ID とパスワードを使用してローカル・リポジトリーから複製やプッシュを行うことはできません。API 要求も、個人用アクセス・トークンを必要とします。

**注:** 認証に個人用アクセス・トークンまたは SSH 鍵を使用するには、ローカルで Git をセットアップする必要があります。説明については、[Setting up Git ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://help.github.com/enterprise/user/articles/set-up-git/){: new_window} を参照してください。    

個人用アクセス・トークンを作成するには、以下の手順に従います。    
   1. 任意の GitHub ページで、プロファイル・アイコンをクリックして、**「設定」**をクリックします。    
   2. サイドバーで、**「個人用アクセス・トークン (Personal access tokens)」**をクリックします。   
   3. **「新規トークンの生成 (Generate new token)」**をクリックします。
   4. トークンの説明を追加して、**「トークンの生成」**をクリックします。
   5. トークンを安全な場所またはパスワード管理アプリケーションにコピーします。    
     **注:** セキュリティー上の理由で、このページから出ると、トークンを再確認できなくなります。    

HTTPS 経由のコマンド・ライン・アクセスには、パスワードの代わりに個人用アクセス・トークンを使用してください。


SSH 鍵を作成するには、以下の手順に従います。
   1. Git Bash (Windows) または新しい端末ウィンドウ (Linux および Mac) を開きます。    
   2. {{site.data.keyword.ghe_short}} アカウントに追加した E メール・アドレスに置き換えて、以下のテキストを貼り付けます。

     ````
     ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
     # Creates a new ssh key, using the provided email as a label
     Generating public/private rsa key pair.
     ````

   3. 鍵を保存するファイルを指定するように求めるプロンプトが出されたら、Enter キーを押して、デフォルト・ロケーションを受け入れます。
   4. プロンプトが出されたら、セキュアなパスフレーズを入力します。詳しくは、[Working with SSH key passphrases ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://help.github.com/enterprise/user/articles/working-with-ssh-key-passphrases/){: new_window} を参照してください。   

以下の手順で、SSH 鍵を ssh-agent に追加します。    
   1. ssh-agent が有効になっていることを確認します。 Git Bash を使用して、次のコマンドを入力して ssh-agent を有効にします。
      ````
      # start the ssh-agent in the background
      $ eval "$(ssh-agent -s)"
      Agent pid 59566
      ````    

   2. 次のコマンドを入力して、SSH 鍵を ssh-agent に追加します。    
      ````
      $ ssh-add ~/.ssh/id_rsa
      ````    
   3. SSH 鍵を GitHub アカウントに追加します。詳しくは、[Adding a new SSH key to your GitHub account ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://help.github.com/enterprise/user/articles/adding-a-new-ssh-key-to-your-github-account/){: new_window} を参照してください。    


{: #ghe_orgs}
## GitHub 組織、チーム、およびリポジトリーのセットアップ    

類似のプロジェクトまたはタスクを担当する別個のユーザー・グループを作成するため、GitHub 組織をセットアップすると役立ちます。組織内にチームを編成すると、リポジトリーへのアクセスを制御するという追加の利点も得られます。詳しくは、[Organizations and teams ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://help.github.com/enterprise/admin/guides/user-management/organizations-and-teams/){: new_window} を参照してください。

**注:** GitHub 組織は {{site.data.keyword.Bluemix_notm}} 組織と同じではありません。

以下のタスクを実行して、チームのプロジェクトをセットアップします。

   1. [組織を作成します ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://help.github.com/enterprise/user/articles/creating-a-new-organization-account/){: new_window}。
   2. [組織のリポジトリーを作成します ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://help.github.com/enterprise/user/articles/create-a-repo/){: new_window}。
   3. [組織に参加するユーザーを招待します ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://help.github.com/articles/inviting-users-to-join-your-organization/){: new_window}。

  **注:** 組織にユーザーを招待する前に、ユーザーは {{site.data.keyword.ghe_short}} に少なくとも 1 回ログインする必要があります。そうしないと、ユーザーの {{site.data.keyword.ghe_short}} アカウントを招待のために使用できません。

<!-- ### Getting support
To get answers now, submit questions to [Stack Overflow ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://stackoverflow.com/questions/ask?tags=ibm-bluemix_github-enterprise){: new_window}.

For more support, use these resources:    
   1. Complete the form at 
   [IBM Cloud Support Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/bluemixsupport) 
   2. Submit a new ticket through the 
   [Client Success Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](
   https://support.ibmcloud.com/ics/support/mylogin.asp?login=bluemix). -->
