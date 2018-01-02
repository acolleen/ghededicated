---

copyright:
  years: 2016, 2017
lastupdated: "2017-12-12"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Iniciación a GitHub Enterprise on IBM Cloud
{: #gheded_getting_started}

GitHub Enterprise on IBM Cloud es la versión totalmente gestionada y alojada de IBM Cloud de {{site.data.keyword.ghe_short}}, disponible para entornos de {{site.data.keyword.Bluemix_notm}} Dedicado. GitHub proporciona la experiencia de codificación social que les gusta a los desarrolladores. [{{site.data.keyword.Bluemix_notm}} Dedicado ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/dedicated/index.html#dedicated){: new_window} proporciona un entorno de computación en la nube en hardware aislado físicamente que se integra en su red.

{{site.data.keyword.ghe_short}} Dedicado es solo para los clientes de {{site.data.keyword.Bluemix_notm}} Dedicado.

{: #ghe_setaccount}
## Configuración de la cuenta

{{site.data.keyword.ghe_short}} incluye un inicio de sesión único con {{site.data.keyword.Bluemix_notm}} Dedicado. Para iniciar sesión en {{site.data.keyword.ghe_short}}, pegue el URL desde el correo electrónico de bienvenida o del administrador de la región en un navegador. El URL seguirá este patrón: `github.your-company-dedicated-name.bluemix.net`. Inicie sesión con el ID de usuario y la contraseña de {{site.data.keyword.Bluemix_notm}} Dedicado. La cuenta de {{site.data.keyword.ghe_short}} se ha creado automáticamente.

**Nota:** Si un mensaje indica que el ID de usuario no existe, pida al administrador de la región que añada el ID de usuario al registro de usuarios de {{site.data.keyword.Bluemix_notm}} Dedicado. Si usted es el administrador de la región, consulte [Gestión de usuarios y permisos de {{site.data.keyword.Bluemix_notm}} Dedicado ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/admin/index.html#oc_useradmin){: new_window}.

En la mayoría de los casos, el nombre de usuario de GitHub es el nombre abreviado del correo electrónico, a menos que el nombre abreviado incluya caracteres a los que GitHub no da soporte, como por ejemplo los puntos. Si el nombre abreviado incluye caracteres a los que GitHub no da soporte, los caracteres se sustituirán por guiones.     

{: #ghe_email}
## Agregar una dirección de correo electrónico a la cuenta

Para recibir notificaciones, debe añadir la dirección de correo electrónico a la configuración de cuenta de {{site.data.keyword.ghe_short}}. Una vez que añada la dirección de correo electrónico, podrá aprovechar las características de codificación social de {{site.data.keyword.ghe_short}}.    

Para añadir la dirección de correo electrónico a la cuenta de {{site.data.keyword.ghe_short}} Dedicado, siga estos pasos:    
1. En cualquier página GitHub, pulse el icono de perfil y, a continuación, pulse **Valores**.    
2. En la barra lateral, pulse **Correos electrónicos**.    
3. Añada la dirección de correo electrónico y pulse **Añadir**.        

{: #ghe_auth}
## Creación de una señal de acceso personal o de una clave SSH para la autenticación

Para realizar operaciones Git remotas, como por ejemplo `clonar` o `enviar por push`, desde el repositorio Git local, debe utilizar una señal de acceso personal o una clave SSH para autenticarse con {{site.data.keyword.ghe_short}}. Se da soporte a la autenticación mediante HTTPS utilizando solo una señal de acceso; no puede utilizar el ID de usuario ni la contraseña para clonar ni enviar por push desde un repositorio local. Las solicitudes de API también requieren una señal de acceso personal.

**Nota:** Para utilizar una señal de acceso personal o una clave SSH para la autenticación, debe configurar Git localmente. Para obtener instrucciones, consulte [Configuración de Git ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://help.github.com/enterprise/user/articles/set-up-git/){: new_window}.    

Para crear una señal de acceso personal, siga estos pasos:    
   1. En cualquier página GitHub, pulse el icono de perfil y, a continuación, pulse **Valores**.    
   2. En la barra lateral, pulse **Señales de acceso personales**.   
   3. Pulse **Generar señal nueva**.
   4. Añada una descripción de señal y pulse **Generar señal**.
   5. Copie la señal a una app de gestión de contraseñas o a una ubicación segura.    
     **Nota:** Por motivos de seguridad, una vez que abandone la página, no podrá ver la señal de nuevo.    

Utilice la señal de acceso personal en lugar de una contraseña para el acceso de la línea de mandatos por HTTPS.


Para crear una clave SSH, siga estos pasos:
   1. Abra Git Bash (Windows) o una nueva ventana de Terminal (Linux y Mac).    
   2. Pegue el texto siguiente, sustituyendo la dirección de correo electrónico que haya añadido a su cuenta de {{site.data.keyword.ghe_short}}:

     ````
     ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
     # Creates a new ssh key, using the provided email as a label
     Generating public/private rsa key pair.
     ````

   3. Cuando se le solicite especificar un archivo en la que guardar la clave, pulse Intro para aceptar la ubicación predeterminada.
   4. En la solicitud, escriba una frase de contraseña segura. Para obtener más información, consulte [Cómo trabajar con frases de contraseña de claves SSH ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://help.github.com/enterprise/user/articles/working-with-ssh-key-passphrases/){: new_window}.   

Añada la clave SSH al ssh-agent:    
   1. Asegúrese de que ssh-agent esté habilitado. Al utilizar Git Bash, especifique este mandato para habilitar el ssh-agent:
      ````
      # start the ssh-agent in the background
      $ eval "$(ssh-agent -s)"
      Agent pid 59566
      ````    

   2. Añada la clave SSH al ssh-agent especificando este mandato:    
      ````
      $ ssh-add ~/.ssh/id_rsa
      ````    
   3. Añada la clave SSH a la cuenta de GitHub. Para obtener más información, consulte [Cómo añadir una nueva clave SSH a la cuenta de GitHub ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://help.github.com/enterprise/user/articles/adding-a-new-ssh-key-to-your-github-account/){: new_window}.    


{: #ghe_orgs}
## Configuración de organizaciones, equipos y repositorios de GitHub    

La configuración de organizaciones de GitHub es útil porque crea grupos de usuarios distintos que trabajan en proyectos o tareas similares. La organización de equipos dentro de una organización tiene el beneficio adicional de controlar el acceso a los repositorios. Para obtener más información, consulte [Organizaciones y equipos ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://help.github.com/enterprise/admin/guides/user-management/organizations-and-teams/){: new_window}.

**Nota:** Las organizaciones de GitHub no son las mismas que las organizaciones de {{site.data.keyword.Bluemix_notm}}.

Configure el proyecto del equipo completando estas tareas:

   1. [Crear una organización (org) ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://help.github.com/enterprise/user/articles/creating-a-new-organization-account/){: new_window}.
   2. [Crear un repositorio para su organización ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://help.github.com/enterprise/user/articles/create-a-repo/){: new_window}.
   3. [Invitar a los usuarios a unirse a su organización ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://help.github.com/articles/inviting-users-to-join-your-organization/){: new_window}.

  **Nota:** Antes de invitar a los usuarios a su organización, deben iniciar sesión en {{site.data.keyword.ghe_short}} al menos una vez o sus cuentas de {{site.data.keyword.ghe_short}} no podrán invitar.

<!-- ### Getting support
To get answers now, submit questions to [Stack Overflow ![External link icon](../../icons/launch-glyph.svg "External link icon")](http://stackoverflow.com/questions/ask?tags=ibm-bluemix_github-enterprise){: new_window}.

For more support, use these resources:    
   1. Complete the form at 
   [IBM Cloud Support Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](https://ibm.biz/bluemixsupport) 
   2. Submit a new ticket through the 
   [Client Success Portal![External link icon](../../icons/launch-glyph.svg "External link icon")](
   https://support.ibmcloud.com/ics/support/mylogin.asp?login=bluemix). -->
