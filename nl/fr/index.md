---

copyright:
  years: 2016, 2017
lastupdated: "2017-12-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Initiation à GitHub Enterprise sur IBM Cloud
{: #gheded_getting_started}

GitHub Enterprise sur IBM Cloud désigne la version hébergée sur IBM Cloud et entièrement gérée de {{site.data.keyword.ghe_short}}, disponible pour les environnements Dedicated {{site.data.keyword.Bluemix_notm}} . GitHub fournit l'expérience de codage social chère aux développeurs. [{{site.data.keyword.Bluemix_notm}} Dedicated ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/dedicated/index.html#dedicated){: new_window} fournit un environnement Cloud Computing sur des matériels isolés physiquement qui sont intégrés à votre réseau.

Dedicated {{site.data.keyword.ghe_short}} est destiné aux clients {{site.data.keyword.Bluemix_notm}} Dedicated uniquement.

{: #ghe_setaccount}
## Configuration de votre compte

{{site.data.keyword.ghe_short}} inclut une connexion unique à {{site.data.keyword.Bluemix_notm}} Dedicated. Pour vous connecter à {{site.data.keyword.ghe_short}}, collez dans un navigateur l'URL fourni par votre administrateur de région ou provenant de votre courrier électronique de bienvenue. L'URL suivra ce schéma : `github.your-company-dedicated-name.bluemix.net`. Connectez-vous avec votre ID utilisateur et votre mot de passe {{site.data.keyword.Bluemix_notm}} Dedicated. Votre compte {{site.data.keyword.ghe_short}} est créé automatiquement.

**Remarque :** Si un message indique que votre ID utilisateur n'existe pas, demandez à votre administrateur régional de l'ajouter au registre d'utilisateurs {{site.data.keyword.Bluemix_notm}} Dedicated. Si vous êtes l'administrateur de la région, voir [Gestion des utilisateurs et des droits dans {{site.data.keyword.Bluemix_notm}} Dedicated ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/admin/index.html#oc_useradmin){: new_window}.

Dans la plupart des cas, votre nom d'utilisateur GitHub correspond à votre nom abrégé d'adresse électronique, sauf si votre nom abrégé inclut des caractères non pris en charge par GitHub, comme les points. Dans ce cas, les caractères non pris en charge sont remplacés par des tirets.     

{: #ghe_email}
## Ajout d'une adresse électronique à votre compte

Pour recevoir des notifications, vous devez ajouter votre adresse de courrier électronique aux paramètres de votre compte {{site.data.keyword.ghe_short}}. Après avoir ajouté votre adresse électronique, vous pouvez tirer parti des fonctions de codage social (social coding) de {{site.data.keyword.ghe_short}}.    

Pour ajouter votre adresse de courrier électronique à votre compte Dedicated {{site.data.keyword.ghe_short}}, procédez comme suit :    
1. Sur n'importe quelle page GitHub, cliquez sur l'icône de votre profil, puis sur **Paramètres**.    
2. Dans la barre de navigation, cliquez sur **Emails**.    
3. Ajoutez votre adresse électronique puis cliquez sur **Add**.        

{: #ghe_auth}
## Création d'un jeton d'accès personnel ou d'une clé SSH pour l'authentification

Pour effectuer des opérations Git à distance, telles que `clone` (clonage) ou `push` (envoi), depuis votre référentiel Git local, vous devez utiliser un jeton d'accès personnel ou une clé SSH pour vous authentifier auprès de {{site.data.keyword.ghe_short}}. L'authentification via HTTPS n'est prise en charge que si vous utilisez un jeton d'accès ; vous ne pouvez pas utiliser votre ID utilisateur et mot de passe pour cloner ou envoyer des images depuis un référentiel local. Les demandes d'API requièrent également un jeton d'accès personnel.

**Remarque :** Pour utiliser un jeton d'accès personnel ou une clé SSH pour l'authentification, vous devez configurer Git en local. Pour les instructions, voir [Configuration de Git![External link icon](../../icons/launch-glyph.svg "External link icon")](https://help.github.com/enterprise/user/articles/set-up-git/){: new_window}.    

Pour créer un jeton d'accès personnel, procédez comme suit :    
   1. Sur n'importe quelle page GitHub, cliquez sur l'icône de votre profil, puis sur **Paramètres**.    
   2. Dans la barre de navigation, cliquez sur **Personal access tokens**.   
   3. Cliquez sur **Generate new token**.
   4. Ajoutez une description du jeton et cliquez sur **Generate token**.
   5. Copiez le jeton sur un emplacement sécurisé ou une application de gestion de mots de passe.    
     **Remarque :** Pour des raisons de sécurité, une fois que vous avez quitté la page, vous ne pouvez plus réafficher le jeton.    

Utilisez votre jeton d'accès personnel à la place d'un mot de passe pour l'accès par ligne de commande via HTTPS.


Pour créer une clé SSH, procédez comme suit :
   1. Ouvrez Git Bash (Windows) ou une nouvelle fenêtre de terminal (Linux et Mac).    
   2. Collez le texte suivant, en indiquant l'adresse électronique que vous avez ajoutée à votre compte {{site.data.keyword.ghe_short}} :

     ````
     ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
     # Creates a new ssh key, using the provided email as a label
     Generating public/private rsa key pair.
     ````

   3. Lorsque vous êtes invité à indiquer un fichier dans lequel sauvegarder la clé, appuyez sur Entrée pour accepter l'emplacement par défaut.
   4. A l'invite, entrez une phrase passe sécurisée. Pour plus d'informations, voir [Working with SSH key passphrases ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://help.github.com/enterprise/user/articles/working-with-ssh-key-passphrases/){: new_window}.   

Ajoutez votre clé SSH à l'agent ssh-agent :    
   1. Assurez-vous que ssh-agent est activé. En utilisant Git Bash, entrez la commande suivante pour activer l'agent ssh-agent :
      ````
      # start the ssh-agent in the background
      $ eval "$(ssh-agent -s)"
      Agent pid 59566
      ````    

   2. Ajoutez votre clé SSH à l'agent ssh-agent en entrant la commande suivante :    
      ````
      $ ssh-add ~/.ssh/id_rsa
      ````    
   3. Ajoutez la clé SSH à votre compte GitHub. Pour plus d'informations, voir [Adding a new SSH key to your GitHub account ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://help.github.com/enterprise/user/articles/adding-a-new-ssh-key-to-your-github-account/){: new_window}.    


{: #ghe_orgs}
## Configuration d'organisations, d'équipes et de référentiels GitHub    

La configuration d'organisations GitHub permet de créer des groupes d'utilisateurs distincts travaillant sur des projets ou des tâches similaires. L'organisation d'équipes au sein d'une organisation présente l'avantage supplémentaire de contrôler l'accès aux référentiels. Pour plus d'informations, voir [Organizations and teams ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://help.github.com/enterprise/admin/guides/user-management/organizations-and-teams/){: new_window}.

**Remarque :** les organisations GitHub ne sont pas les mêmes que les organisations {{site.data.keyword.Bluemix_notm}}.

Configurez le projet de votre équipe en procédant comme suit :

   1. [Créez une organisation (org) ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://help.github.com/enterprise/user/articles/creating-a-new-organization-account/){: new_window}.
   2. [Créez un référentiel pour votre organisation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://help.github.com/enterprise/user/articles/create-a-repo/){: new_window}.
   3. [Invitez des utilisateurs à rejoindre votre organisation ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://help.github.com/articles/inviting-users-to-join-your-organization/){: new_window}.

  **Remarque :** avant d'inviter des utilisateurs dans votre organisation, ils doivent se connecter au moins une fois à {{site.data.keyword.ghe_short}}, sans quoi leurs comptes {{site.data.keyword.ghe_short}} ne seront pas disponibles pour une invitation.

<!-- ### Getting support
To get answers now, submit questions to [Stack Overflow ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://stackoverflow.com/questions/ask?tags=ibm-bluemix_github-enterprise){: new_window}.

For more support, use these resources:    
   1. Complete the form at 
   [IBM Cloud Support Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/bluemixsupport) 
   2. Submit a new ticket through the 
   [Client Success Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](
   https://support.ibmcloud.com/ics/support/mylogin.asp?login=bluemix). -->
