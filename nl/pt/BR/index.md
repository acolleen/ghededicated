---

copyright:
  years: 2016, 2017
lastupdated: "2017-12-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Introdução ao GitHub Enterprise on IBM Cloud
{: #gheded_getting_started}

O GitHub Enterprise on IBM Cloud é a versão totalmente gerenciada e hospedada pelo IBM Cloud do {{site.data.keyword.ghe_short}}, disponível para ambientes do {{site.data.keyword.Bluemix_notm}} Dedicated. O GitHub fornece a experiência de codificação social que os desenvolvedores amam. O [{{site.data.keyword.Bluemix_notm}} Dedicated ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/dedicated/index.html#dedicated){: new_window} fornece um ambiente de computação em nuvem em hardware fisicamente isolado que é integrado à sua rede.

O Dedicated {{site.data.keyword.ghe_short}} é para clientes {{site.data.keyword.Bluemix_notm}} Dedicated somente.

{: #ghe_setaccount}
## Configurando sua conta

O {{site.data.keyword.ghe_short}} inclui a conexão única com o {{site.data.keyword.Bluemix_notm}} Dedicated. Para efetuar
login no {{site.data.keyword.ghe_short}}, cole a URL de seu administrador de região ou e-mail de boas-vindas em um navegador. A URL seguirá este padrão: `github.your-company-dedicated-name.bluemix.net`. Conecte-se com seu ID de usuário e sua senha do {{site.data.keyword.Bluemix_notm}} Dedicated. Sua conta do {{site.data.keyword.ghe_short}} é criada automaticamente.

**Nota:** se uma mensagem declarar que seu ID do usuário não existe, solicite ao seu administrador de região que inclua seu ID do usuário no registro do usuário do {{site.data.keyword.Bluemix_notm}} Dedicated. Se você for o administrador da região, consulte [Gerenciando usuários e permissões do {{site.data.keyword.Bluemix_notm}} Dedicated ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/admin/index.html#oc_useradmin){: new_window}.

Na maioria dos casos, seu nome de usuário GitHub é seu nome abreviado de e-mail, a menos que seu nome abreviado inclua caracteres que o
GitHub não suporte, como pontos. Se seu nome abreviado incluir caracteres que o GitHub não suportar, os caracteres serão substituídos por traços.     

{: #ghe_email}
## Incluindo um endereço de e-mail em sua conta

Para receber notificações, deve-se incluir seu endereço de e-mail nas configurações da conta do {{site.data.keyword.ghe_short}}. Após incluir seu endereço de e-mail, você aproveita os recursos de codificação social do {{site.data.keyword.ghe_short}}.    

Para incluir seu endereço de e-mail em sua conta do {{site.data.keyword.ghe_short}} Dedicated, siga estas etapas:    
1. Em qualquer página do GitHub, clique em seu ícone do perfil e, em seguida, clique em **Configurações**.    
2. Na barra lateral, clique em **E-mails**.    
3. Inclua seu endereço de e-mail e clique em **Incluir**.        

{: #ghe_auth}
## Criando um token de acesso pessoal ou chave SSH para autenticação

Para executar operações Git remotas, como `clone` ou `push`, em seu repositório Git local, deve-se usar um token de acesso pessoal ou uma chave SSH para autenticar com o {{site.data.keyword.ghe_short}}. A autenticação por meio de HTTPS é suportada somente com o uso de um token de acesso. Não é possível usar o ID de usuário e a senha para clonar ou enviar por push de um repositório local. As solicitações de API também requerem um token de acesso pessoal.

**Nota:** para usar um token de acesso pessoal ou chave SSH para autenticação, deve-se configurar o Git localmente. Para obter instruções, consulte [Configurando o Git ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://help.github.com/enterprise/user/articles/set-up-git/){: new_window}.    

Para criar um token de acesso pessoal, siga estas etapas:    
   1. Em qualquer página do GitHub, clique em seu ícone do perfil e, em seguida, clique em **Configurações**.    
   2. Na barra lateral, clique em **Tokens de acesso pessoal**.   
   3. Clique em **Gerar novo token**.
   4. Inclua uma descrição de token e clique em **Gerar token**.
   5. Copie o token em um local seguro ou app de gerenciamento de senha.    
     **Nota:** por motivos de segurança, após deixar a página, não será mais possível ver o token novamente.    

Use seu token de acesso pessoal em vez de uma senha para o acesso da linha de comandos por HTTPS.


Para criar uma chave SSH, siga estas etapas:
   1. Abra o Git Bash (Windows) ou uma nova janela do Terminal (Linux e Mac).    
   2. Cole o texto a seguir, substituindo o endereço de e-mail que incluiu em sua conta {{site.data.keyword.ghe_short}}:

     ````
     ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
     # Creates a new ssh key, using the provided email as a label
     Generating public/private rsa key pair.
     ````

   3. Quando for solicitado que especifique um arquivo para salvar a chave, pressione Enter para aceitar o local padrão.
   4. No prompt, digite um passphrase seguro. Para obter mais informações, consulte [Trabalhando com passphrases da chave SSH ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://help.github.com/enterprise/user/articles/working-with-ssh-key-passphrases/){: new_window}.   

Inclua sua chave SSH no ssh-agent:    
   1. Assegure-se de que o ssh-agent esteja ativado. Usando o Git Bash, insira este comando para ativar o ssh-agent:
      ````
      # start the ssh-agent in the background
      $ eval "$(ssh-agent -s)"
      Agent pid 59566
      ````    

   2. Inclua sua chave SSH no ssh-agent inserindo este comando:    
      ````
      $ ssh-add ~/.ssh/id_rsa
      ````    
   3. Inclua a chave SSH em sua conta GitHub. Para obter mais informações, consulte [Incluindo uma nova chave SSH em sua conta do GitHub ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://help.github.com/enterprise/user/articles/adding-a-new-ssh-key-to-your-github-account/){: new_window}.    


{: #ghe_orgs}
## Configurando organizações, equipes e repos GitHub    

Configurar organizações GitHub é útil porque você cria grupos distintos de usuários que trabalham em projetos ou tarefas semelhantes. Organizar
equipes em uma organização tem o benefício agregado de controlar o acesso a repos. Para obter mais informações, consulte [Organizações e equipes ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://help.github.com/enterprise/admin/guides/user-management/organizations-and-teams/){: new_window}.

**Observação:** as organizações do GitHub não são as mesmas que as organizações do {{site.data.keyword.Bluemix_notm}}.

Configure o projeto de sua equipe concluindo estas etapas:

   1. [Crie uma organização (org) ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://help.github.com/enterprise/user/articles/creating-a-new-organization-account/){: new_window}.
   2. [Crie um repositório para sua organização ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://help.github.com/enterprise/user/articles/create-a-repo/){: new_window}.
   3. [Convide usuários a se juntarem à sua organização ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://help.github.com/articles/inviting-users-to-join-your-organization/){: new_window}.

  **Observação:** antes de convidar usuários para a sua organização, eles devem efetuar login no {{site.data.keyword.ghe_short}} pelo menos uma vez ou suas contas do {{site.data.keyword.ghe_short}} não estarão disponíveis para o convite.

<!-- ### Getting support
To get answers now, submit questions to [Stack Overflow ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://stackoverflow.com/questions/ask?tags=ibm-bluemix_github-enterprise){: new_window}.

For more support, use these resources:    
   1. Complete the form at 
   [IBM Cloud Support Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/bluemixsupport) 
   2. Submit a new ticket through the 
   [Client Success Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](
   https://support.ibmcloud.com/ics/support/mylogin.asp?login=bluemix). -->
