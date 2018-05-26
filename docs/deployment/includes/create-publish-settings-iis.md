
1. Fermez et rouvrez la Console de gestion IIS pour afficher les options de configuration mis à jour dans l’interface utilisateur.

1. Dans IIS, cliquez sur le **Site Web par défaut**, choisissez **déployer** > **configuration Web déployer de la publication**.

    ![Configurer la configuration de déploiement Web](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. Dans le **configuration Web déployer de la publication** boîte de dialogue zone, examinez les paramètres.

1. Cliquez sur **le programme d’installation**.

    Dans le **résultats** Panneau de configuration, la sortie montre que les droits d’accès est accordée à l’utilisateur spécifié et à qui un fichier avec un *.publishsettings* extension de fichier a été générée à l’emplacement indiqué dans la boîte de dialogue zone.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    Selon votre configuration de Windows Server et les services IIS, vous voyez des valeurs différentes dans le fichier XML. Voici quelques détails sur les valeurs que vous voyez :

    * Le *msdeploy.axd* fichier référencé dans le `publishUrl` attribut est un fichier de gestionnaire HTTP généré de manière dynamique pour Web Deploy. (Pour des tests, `http://myhostname:8172` généralement fonctionne également.)
    * Le `publishUrl` port est défini sur le port 8172, qui est la valeur par défaut pour Web Deploy.
    * Le `destinationAppUrl` port est défini sur le port 80, qui est la valeur par défaut pour IIS.
    * Si vous ne parvenez pas à se connecter à l’hôte distant dans Visual Studio en utilisant le nom d’hôte (dans les étapes suivantes), testez l’adresse IP à la place du nom d’hôte.

    > [!NOTE]
    > Si vous publiez sur IIS qui s’exécute sur une machine virtuelle Azure, vous devez ouvrir les ports IIS et Web Deploy dans le groupe de sécurité réseau. Pour plus d’informations, consultez [installer et exécuter IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

1. Copiez ce fichier sur l’ordinateur sur lequel vous exécutez Visual Studio.
