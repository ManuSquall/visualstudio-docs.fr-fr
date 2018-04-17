---
title: ASP.NET sur un ordinateur distant IIS de débogage à distance | Documents Microsoft
ms.custom: remotedebugging
ms.date: 07/26/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 1c8d2cfb57d3e96b845bc243575eb63af88720c0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Débogage distant ASP.NET sur un ordinateur distant IIS
Pour déboguer une application ASP.NET qui a été déployée sur IIS, installer et exécuter les outils à distance sur l’ordinateur où vous avez déployé votre application puis attachez à votre application en cours d’exécution à partir de Visual Studio.

![Composants du débogueur distant](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Ce guide explique comment installer et configurer une application Visual Studio 2017 ASP.NET MVC 4.5.2, déployez-le sur IIS et attacher le débogueur distant à partir de Visual Studio. Pour déboguer à distance ASP.NET Core, consultez [Core d’ASP.NET déboguer à distance sur un ordinateur IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Pour le Service d’applications Azure, vous pouvez facilement déployer et déboguer sur une instance préconfigurée de IIS à l’aide du [instantané débogueur](../debugger/debug-live-azure-applications.md) (.NET 4.6.1 requis) ou par [attacher le débogueur à partir de l’Explorateur de serveurs](../debugger/remote-debugging-azure.md).

Ces procédures ont été testées sur ces configurations de serveur :
* Windows Server 2012 R2 et IIS 8 (pour Windows Server 2008 R2, les étapes de serveur sont différentes)

## <a name="requirements"></a>Spécifications

Le débogueur distant est pris en charge sur Windows Server depuis Windows Server 2008 Service Pack 2. Pour obtenir une liste complète des conditions requises, consultez [exigences](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Débogage entre deux ordinateurs connectés via un proxy n’est pas pris en charge. Débogage sur une latence élevée ou d’une connexion à faible bande passante, telles que les connexions à distance d’Internet, ou via Internet entre des pays n’est pas recommandé et peut échouer ou être trop faibles.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Créer ASP.NET 4.5.2 application sur l’ordinateur Visual Studio
  
1. Créez une application ASP.NET MVC. (**Fichier > Nouveau > projet**, puis sélectionnez ** Visual c# > Web > Application Web ASP.NET. Dans la section des modèles **ASP.NET 4.5.2** , sélectionnez **MVC**. Assurez-vous que **activer la prise en charge Docker** n’est pas sélectionnée et que **authentification** a la valeur **aucune authentification**. Nommez le projet **MyASPApp**.)

2. Ouvrez le fichier HomeController.cs et définissez un point d’arrêt dans la méthode `About()` .

## <a name="bkmk_configureIIS"></a> Installer et configurer IIS sur Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Mettre à jour les paramètres de sécurité de navigateur sur Windows Server

En fonction de vos paramètres de sécurité, il peut gagner du temps d’ajouter les sites de confiance suivants à votre navigateur vous pouvez facilement télécharger le logiciel décrit dans ce didacticiel. Accès à ces sites peuvent être nécessaires :

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- visualstudio.com

Si vous utilisez Internet Explorer, vous pouvez ajouter les sites de confiance en accédant à **Options Internet > sécurité > Sites de confiance > Sites**. Ces étapes sont différents pour d’autres navigateurs. (Si vous avez besoin télécharger une version antérieure du débogueur distant à partir de my.visualstudio.com, certains sites de confiance supplémentaires sont requis pour se connecter).

Lorsque vous téléchargez le logiciel, vous pouvez obtenir des demandes pour accorder des autorisations requises pour charger les différents scripts de site web et des ressources. Dans la plupart des cas, les ressources supplémentaires suivantes ne sont pas requis pour installer le logiciel.

## <a name="BKMK_deploy_asp_net"></a> Installez ASP.NET 4.5 sur Windows Server

Si vous souhaitez des informations plus détaillées pour installer ASP.NET sur IIS, consultez [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Web Platform Installer (WebPI) permet d’installer ASP.NET 4.5 (à partir du nœud de serveur dans Windows Server 2012 R2, choisissez **obtenir nouveaux composants Web Platform** , puis recherchez ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Si vous utilisez Windows Server 2008 R2, installez ASP.NET 4 au lieu d’utiliser cette commande :

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Redémarrer le système (ou exécutez **net stop a été /y** suivie **net démarrer w3svc** à partir d’une invite de commandes pour voir une modification dans le chemin d’accès du système).

## <a name="BKMK_install_webdeploy"></a> (Facultatif) Installation Web déployer 3.6 sur Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a> Configurer le site Web ASP.NET sur l’ordinateur Windows Server

1. Ouvrez l’Explorateur Windows et créez un dossier, **C:\Publish**, où vous déploierez plus tard le projet ASP.NET.

2. Ouvrez le **Internet Information Services (IIS) Manager**. (Dans le volet gauche du Gestionnaire de serveur, sélectionnez **IIS**. Cliquez sur le serveur et sélectionnez **Gestionnaire des Services Internet (IIS)**.)

3. Sous **connexions** dans le volet gauche, accédez à **Sites**.

4. Sélectionnez le **Site Web par défaut**, choisissez **les paramètres de base**et définissez la **chemin d’accès physique** à **C:\Publish**.

5. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.

6. Définir le **Alias** au champ **MyASPApp**, acceptez la valeur par défaut du Pool d’applications (**DefaultAppPool**) et définissez la **chemin d’accès physique** à  **C:\Publish**.

7. Sous **connexions**, sélectionnez **Pools d’applications**. Ouvrez **DefaultAppPool** et la valeur du champ de pool d’applications **ASP.NET v4.0** (ASP.NET 4.5 n’est pas une option pour le pool d’applications).

8. Le site sélectionné dans le Gestionnaire des services Internet, choisissez **modifier les autorisations**et assurez-vous que IUSR, IIS_IUSRS ou l’utilisateur configuré pour le Pool d’applications est un utilisateur autorisé avec des droits de lecture et exécution. Si aucun de ces utilisateurs sont présentes, ajoutez IUSR en tant qu’utilisateur avec des droits de lecture et exécution.

## <a name="bkmk_webdeploy"></a> (Facultatif) Publier et déployer l’application à l’aide de Web Deploy à partir de Visual Studio

[!INCLUDE [remote-debugger-deploy-app-web-deploy](../debugger/includes/remote-debugger-deploy-app-web-deploy.md)]

En outre, vous devez lire la section sur [résolution des problèmes de ports](#bkmk_openports).

## <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Facultatif) Publier et déployer l’application en publiant dans un dossier local à partir de Visual Studio

Vous pouvez également publier et déployer l’application à l’aide du système de fichiers ou d’autres outils.

1. (ASP.NET 4.5.2) Assurez-vous que le fichier web.config indique la version correcte du .NET Framework.  Par exemple, si vous ciblez ASP.NET 4.5.2, assurez-vous que cette version est répertoriée dans le fichier web.config.
  
    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>
  
    ```

    Par exemple, la version doit être 4.0 si vous installez ASP.NET 4 au lieu de 4.5.2.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a> Téléchargez et installez les outils à distance sur Windows Server

Dans ce didacticiel, nous utilisons Visual Studio 2017.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> Dans certains scénarios, il peut être plus efficace d’exécuter le débogueur distant à partir d’un partage de fichiers. Pour plus d’informations, consultez [exécuter le débogueur distant à partir d’un partage de fichiers](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a> Configurer le débogueur distant sur Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si vous devez ajouter des autorisations pour les utilisateurs supplémentaires, modifier le mode d’authentification ou numéro de port pour le débogueur distant, consultez [configurer le débogueur distant](../debugger/remote-debugging.md#configure_msvsmon).

Pour plus d’informations sur l’exécution du débogueur distant en tant que service, consultez [exécuter le débogueur distant en tant que service](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Attachement à l’application ASP.NET à partir de l’ordinateur Visual Studio

1. Sur l’ordinateur Visual Studio, ouvrez le **MyASPApp** solution.
2. Dans Visual Studio, cliquez sur **Déboguer > Attacher au processus** (Ctrl + Alt + P).

    > [!TIP]
    > Dans Visual Studio 2017, vous pouvez rattacher au même processus vous précédemment attaché à l’aide de **Déboguer > rattacher à un processus en cours...** (Maj + Alt + P). 

3. Définissez le champ qualificateur sur  **\<nom_ordinateur_distant > : 4022**.
4. Cliquez sur **Actualiser**.
    Des processus doivent s’afficher dans la fenêtre **Processus disponibles** .

    Si vous ne voyez pas tous les processus, essayez d’utiliser l’adresse IP au lieu du nom de l’ordinateur distant (le port est requis). Vous pouvez utiliser `ipconfig` dans une ligne de commande pour obtenir l’adresse IPv4.

5. Cochez  **Afficher les processus de tous les utilisateurs**.
6. Tapez la première lettre d’un nom de processus pour rechercher rapidement **w3wp.exe** pour ASP.NET 4.5.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess.png "RemoteDBG_AttachToProcess")

7. Cliquez sur **attacher**

8. Ouvrez le site web de l’ordinateur distant. Dans un navigateur, accédez à **http://\<nom_ordinateur_distant >**.
    
    La page web ASP.NET doit s’afficher.
9. Dans l’application ASP.NET en cours d’exécution, cliquez sur le lien vers le **sur** page.

    Le point d’arrêt doit être atteint dans Visual Studio.

## <a name="bkmk_openports"></a> Résolution des problèmes : Ouvrir les ports requis sur Windows Server

Dans la plupart des configurations, les ports requis sont ouverts par l’installation d’ASP.NET et le débogueur distant. Toutefois, vous devrez peut-être vérifier que les ports sont ouverts.

> [!NOTE]
> Sur une machine virtuelle Azure, vous devez ouvrir les ports via la [groupe de sécurité réseau](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Ports requis :

- 80 - requis pour IIS
- 8172 - (facultatif) requis pour Web Deploy déployer l’application à partir de Visual Studio
- 4022 - requis pour le débogage distant à partir de Visual Studio 2017 (consultez [affectations de Port du débogueur distant](../debugger/remote-debugger-port-assignments.md) pour plus d’informations.
- UDP 3702 - port de détection de (facultatif) vous permet du **trouver** bouton lors de l’attachement du débogueur distant dans Visual Studio.

1. Pour ouvrir un port sur Windows Server, ouvrez le **Démarrer** menu, recherchez **pare-feu Windows avec fonctions avancées de sécurité**.

2. Puis choisissez **règles de trafic entrant > nouvelle règle > Port**. Choisissez **suivant** et sous **ports locaux spécifiques**, entrez le numéro de port, cliquez sur **suivant**, puis **autoriser la connexion**, cliquez sur Suivant, et Ajoutez le nom (**IIS**, **Web Deploy**, ou **msvsmon**) pour la règle de trafic entrant.

    Si vous souhaitez plus d’informations sur la configuration du pare-feu Windows, consultez [configurer le pare-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Créer des règles supplémentaires pour les autres ports requis.