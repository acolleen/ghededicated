---

copyright:
  years: 2016, 2017
lastupdated: "2017-12-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# GitHub Enterprise on IBM Cloud - Einführung
{: #gheded_getting_started}

GitHub Enterprise on IBM Cloud ist die in IBM Cloud bereitgestellte und vollständig verwaltete Version von {{site.data.keyword.ghe_short}}, die für Dedicated {{site.data.keyword.Bluemix_notm}}-Umgebungen verfügbar ist. GitHub bietet die von Entwicklern gewünschte Social Coding Experience. [{{site.data.keyword.Bluemix_notm}} Dedicated ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/dedicated/index.html#dedicated){: new_window} stellt eine Cloud-Computing-Umgebung auf physisch isolierter Hardware bereit, die in Ihr Netz integriert wird. 

Dedicated {{site.data.keyword.ghe_short}} steht nur für {{site.data.keyword.Bluemix_notm}} Dedicated-Kunden zur Verfügung.

{: #ghe_setaccount}
## Konto einrichten

{{site.data.keyword.ghe_short}} bietet Single Sign-on mit {{site.data.keyword.Bluemix_notm}} Dedicated. Für die Anmeldung bei {{site.data.keyword.ghe_short}} fügen Sie die URL, die Sie vom Regionsadministrator oder in der Begrüßungs-E-Mail erhalten haben, in einen Browser ein. Die URL weist das folgende Muster auf: `github.your-company-dedicated-name.bluemix.net`. Melden Sie sich mit Ihrer {{site.data.keyword.Bluemix_notm}} Dedicated-Benutzer-ID und dem entsprechenden Kennwort an. Ihr {{site.data.keyword.ghe_short}}-Konto wird automatisch erstellt.

**Hinweis:** Wenn Sie in einer Nachricht darüber informiert werden, dass Ihre Benutzer-ID nicht vorhanden ist, bitten Sie den zuständigen Regionsadministrator, Ihre Benutzer-ID zur Benutzerregistry von {{site.data.keyword.Bluemix_notm}} Dedicated hinzuzufügen. Als Regionsadministrator finden Sie die entsprechenden Informationen in [Benutzer und Berechtigungen in {{site.data.keyword.Bluemix_notm}} Dedicated verwalten![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/admin/index.html#oc_useradmin){: new_window}.

In den meisten Fällen ist Ihr GitHub-Benutzername Ihr E-Mail-Kurzname, es sei denn, der Kurzname enthält Zeichen, die von GitHub nicht unterstützt werden, wie z. B. Punkte. Wenn der Kurzname Zeichen enthält, die von GitHub nicht unterstützt werden, werden diese Zeichen durch Gedankenstriche ersetzt.     

{: #ghe_email}
## E-Mail-Adresse zum Konto hinzufügen

Für das Empfangen von Benachrichtigungen müssen Sie Ihre E-Mail-Adresse zu Ihren Kontoeinstellungen für {{site.data.keyword.ghe_short}} hinzufügen. Nach dem Hinzufügen der E-Mail-Adresse können Sie die Social Coding-Features von {{site.data.keyword.ghe_short}} nutzen.    

Zum Hinzufügen der E-Mail-Adresse zum Dedicated {{site.data.keyword.ghe_short}}-Konto führen Sie die folgenden Schritte aus:    
1. Klicken Sie auf einer beliebigen GitHub-Seite auf das Symbol für Ihr Profil und dann auf **Einstellungen**.    
2. Klicken Sie in der seitliche Leiste auf **E-Mails**.    
3. Fügen Sie die E-Mail-Adresse hinzu und klicken Sie auf **Hinzufügen**.        

{: #ghe_auth}
## Persönliches Zugriffstoken oder SSH-Schlüssel für die Authentifizierung erstellen

Wenn Sie ferne Git-Operationen wie `clone` oder `push` über Ihr lokales Git-Repository durchführen möchten,  müssen Sie ein persönliches Zugriffstoken oder einen SSH-Schlüssel für die Authentifizierung bei {{site.data.keyword.ghe_short}} verwenden. Die Authentifizierung über HTTPS wird nur mit der Verwendung eines Zugriffstokens unterstützt; es ist nicht möglich, die Benutzer-ID für clone- oder push-Operationen über ein lokales Repository zu verwenden. Für API-Anforderungen ist ebenfalls ein persönliches Zugriffstoken erforderlich.

**Hinweis:** Wenn Sie ein persönliches Zugriffstoken oder einen SSH-Schlüssel für die Authentifizierung verwenden möchten, müssen Sie Git lokal einrichten. Eine Anleitung finden Sie in [Git einrichten ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://help.github.com/enterprise/user/articles/set-up-git/){: new_window}.    

Zum Erstellen eines persönlichen Zugriffstokens führen Sie die folgenden Schritte aus:    
   1. Klicken Sie auf einer beliebigen GitHub-Seite auf das Symbol für Ihr Profil und dann auf **Einstellungen**.    
   2. Klicken Sie in der seitliche Leiste auf **Persönliche Zugriffstokens**.   
   3. Klicken Sie auf **Neues Token generieren**.
   4. Fügen Sie eine Beschreibung für das Token hinzu und klicken Sie auf **Token generieren**.
   5. Kopieren Sie das Token an eine sichere Position oder in eine Kennwortmanagement-App.    
     **Hinweis:** Nach dem Verlassen der Seite kann das Token aus Sicherheitsgründen nicht erneut angezeigt werden.    

Verwenden Sie für den Befehlszeilenzugriff über HTTPS Ihr persönliches Zugriffstoken anstelle eines Kennworts.


Zum Erstellen eines SSH-Schlüssels führen Sie die folgenden Schritte aus:
   1. Öffnen Sie Git Bash (Windows) oder ein neues Terminalfenster (Linux und Mac).    
   2. Fügen Sie den folgenden Text ein und verwenden Sie dabei die E-Mail-Adresse, die Sie zu Ihrem {{site.data.keyword.ghe_short}}-Konto hinzugefügt haben:

     ````
     ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
     # Erstellt einen neuen SSH-Schlüssel mit der angegebenen E-Mail-Adresse als Bezeichnung.
     Generieren eines RSA-Schlüsselpaars aus öffentlichem/privatem Schlüssel.
     ````

   3. Wenn Sie dazu aufgefordert werden, eine Datei zum Speichern des Schlüssels anzugeben, drücken Sie die Eingabetaste, um die Standardposition zu akzeptieren.
   4. Geben Sie eine sichere Kennphrase in der Eingabeaufforderung ein. Weitere Informationen finden Sie in [Mit Kennphrasen für SSH-Schlüssel arbeiten![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://help.github.com/enterprise/user/articles/working-with-ssh-key-passphrases/){: new_window}.   

Fügen Sie Ihren SSH-Schlüssel zum SSH-Agenten hinzu:    
   1. Stellen Sie sicher, dass der SSH-Agent aktiviert ist. Verwenden Sie Git Bash, um diesen Befehl zur Aktivierung des SSH-Agenten einzugeben:
      ````
      # SSH-Agent im Hintergrund starten
      $ eval "$(ssh-agent -s)"
      Agent pid 59566
      ````    

   2. Fügen Sie Ihren SSH-Schlüssel zum SSH-Agenten hinzu, indem Sie den folgenden Befehl eingeben:    
      ````
      $ ssh-add ~/.ssh/id_rsa
      ````    
   3. Fügen Sie den SSH-Schlüssel zu Ihrem GitHub-Konto hinzu. Weitere Informationen finden Sie in [Neuen SSH-Schlüssel zum GitHub-Konto hinzufügen![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://help.github.com/enterprise/user/articles/adding-a-new-ssh-key-to-your-github-account/){: new_window}.    


{: #ghe_orgs}
## GitHub-Organisationen, -Teams und Repositorys einrichten    

Das Einrichten von GitHub-Organisationen ist nützlich, da auf diese Weise eine individuelle Gruppe von Benutzern erstellt wird, die an ähnlichen Projekten oder Tasks arbeiten. Das Organisieren von Teams innerhalb einer Organisation bietet darüber hinaus den Vorteil der Zugriffssteuerung für Repositorys. Weitere Informationen finden Sie in [Organisationen und Teams ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://help.github.com/enterprise/admin/guides/user-management/organizations-and-teams/){: new_window}.

**Hinweis:** GitHub-Organisation sind nicht identisch mit {{site.data.keyword.Bluemix_notm}}-Organisationen.

Führen Sie die folgenden Tasks aus, um das Projekt Ihres Teams einzurichten:

   1. [Organisation (org) erstellen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://help.github.com/enterprise/user/articles/creating-a-new-organization-account/){: new_window}.
   2. [Repository für die Organisation erstellen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://help.github.com/enterprise/user/articles/create-a-repo/){: new_window}.
   3. [Benutzer zur Teilnahme an der Organisation einladen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://help.github.com/articles/inviting-users-to-join-your-organization/){: new_window}.

  **Hinweis:** Bevor Sie Benutzer zur Organisation einladen, müssen diese sich mindestens einmal bei {{site.data.keyword.ghe_short}} anmelden, da andernfalls ihre {{site.data.keyword.ghe_short}}-Konten nicht für Einladungen zur Verfügung stehen.

<!-- ### Getting support
To get answers now, submit questions to [Stack Overflow ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://stackoverflow.com/questions/ask?tags=ibm-bluemix_github-enterprise){: new_window}.

For more support, use these resources:    
   1. Complete the form at 
   [IBM Cloud Support Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/bluemixsupport) 
   2. Submit a new ticket through the 
   [Client Success Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](
   https://support.ibmcloud.com/ics/support/mylogin.asp?login=bluemix). -->
