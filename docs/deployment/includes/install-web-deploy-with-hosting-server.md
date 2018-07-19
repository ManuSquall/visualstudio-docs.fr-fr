Web Deploy 3.6 pour les serveurs d’hébergement fournit les fonctionnalités de configuration supplémentaires qui permettent la création du fichier de paramètres de publication à partir de l’interface utilisateur.

1. Si vous avez Web déployer 3.6 est déjà installé sur Windows Server, désinstallez-le à l’aide de **le panneau de configuration** > **programmes** > **désinstaller un programme**.

1. Ensuite, installez 3.6 de déploiement Web pour les serveurs d’hébergement sur Windows Server.

    Pour installer Web Deploy pour les serveurs d’hébergement, utilisez le [Web Platform Installer (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). (Pour rechercher le lien de Web Platform Installer à partir d’IIS, sélectionnez **IIS** dans le volet gauche du Gestionnaire de serveur. Cliquez sur le serveur et sélectionnez **Internet Information Services (IIS) Manager**.)

    Dans le programme Web Platform Installer, vous recherchez **Web Deploy pour les serveurs d’hébergement** sous l’onglet Applications.

1. Si vous avez déjà installé **gestion des Scripts et outils IIS**, installez-le maintenant.

    Accédez à **sélectionner des rôles de serveur** > **serveur Web (IIS)** > **outils de gestion**, puis sélectionnez le **des Scripts de gestion IIS Outils et** rôle, cliquez sur **suivant**, puis installer le rôle.

    ![Installer les outils et les Scripts de gestion IIS](../../deployment/media/tutorial-iis-management-scripts-and-tools.png)

    Les scripts et les outils sont requis pour activer la génération du fichier de paramètres de publication.

1. (Facultatif) Vérifiez que Web Deploy s’exécute correctement en ouvrant **le panneau de configuration > système et sécurité > Outils d’administration > Services** et assurez-vous que l’option **Service de l’Agent de déploiement Web** est en cours d’exécution (le nom du service est différent dans les versions antérieures).

    Si le service agent n’est pas en cours d’exécution, démarrez-le. Si elle ne figure pas du tout, accédez à **le panneau de configuration > Programmes > désinstaller un programme**, recherchez **Microsoft Web Deploy <version>** . Choisissez de **modification** l’installation et vérifiez que vous choisissez **sera installé sur le disque dur local** pour les composants Web Deploy. Effectuez les étapes d’installation de modification.