---
title: Déboguer à distance ASP.NET sur un ordinateur IIS
ms.custom:
- remotedebugging
- seodec18
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: ba255d1d1e906e8fe7bacd05d1f4afd4b7bf413b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63407844"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Déboguer à distance ASP.NET sur un ordinateur distant IIS
Pour déboguer une application ASP.NET qui a été déployée sur IIS, installer et exécuter les outils à distance sur l’ordinateur où vous avez déployé votre application, puis attacher à votre application en cours d’exécution à partir de Visual Studio.

![Composants du débogueur distant](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Ce guide explique comment paramétrer et configurer une application Visual Studio ASP.NET MVC 4.5.2, déployez-le sur IIS et attacher le débogueur distant à partir de Visual Studio.

> [!NOTE]
> À distance à la place de débogage ASP.NET Core, consultez [à distance déboguer ASP.NET Core sur un ordinateur IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Pour Azure App Service, vous pouvez facilement déployer et déboguer sur une instance préconfigurée d’IIS à l’aide du [débogueur de capture instantanée](../debugger/debug-live-azure-applications.md) (.NET 4.6.1 requise) ou par [attacher le débogueur à partir de l’Explorateur de serveurs](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Prérequis

::: moniker range=">=vs-2019"
Visual Studio 2019 est nécessaire pour suivre les étapes indiquées dans cet article.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 est nécessaire pour suivre les étapes indiquées dans cet article.
::: moniker-end

Ces procédures ont été testées sur ces configurations de serveur :
* Windows Server 2012 R2 et IIS 8 (pour Windows Server 2008 R2, les étapes de serveur sont différents)

## <a name="network-requirements"></a>Configuration réseau requise

Le débogueur distant est pris en charge sur Windows Server depuis Windows Server 2008 Service Pack 2. Pour obtenir une liste complète des exigences, consultez [exigences](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Débogage entre deux ordinateurs connectés via un proxy n’est pas pris en charge. Débogage sur une latence élevée ou faible bande passante, telles que la numérotation Internet, ou via Internet entre les pays n’est pas recommandé et peut échouer ou être trop faibles.

## <a name="app-already-running-in-iis"></a>Application déjà en cours d’exécution dans IIS ?

Cet article contient des instructions sur la configuration d’une configuration de base d’IIS sur Windows server et le déploiement de l’application à partir de Visual Studio. Ces étapes sont inclus pour vous assurer que le serveur a exigé des composants installés, que l’application peut s’exécuter correctement et que vous êtes prêt à déboguer à distance.

* Si votre application s’exécute dans IIS et que vous souhaitez simplement télécharger le débogueur distant et démarrer le débogage, accédez à [télécharger et installer les outils à distance sur Windows Server](#BKMK_msvsmon).

* Si vous souhaitez une aide pour vous assurer que votre application est configurée, déployé et fonctionne correctement dans IIS afin que vous puissiez déboguer, suivez les étapes dans cette rubrique.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Créer l’ASP.NET 4.5.2 application sur l’ordinateur Visual Studio

1. Créez une application ASP.NET MVC.

    ::: moniker range=">=vs-2019"
    Dans Visual Studio 2019, tapez **Ctrl + Q** pour ouvrir la zone de recherche, tapez **asp.net**, choisissez **modèles**, puis choisissez **créer nouveau ASP.NET Web Application (.NET Framework)**. Dans la boîte de dialogue qui s’affiche, nommez le projet **MyASPApp**, puis choisissez **créer**. Sélectionnez **MVC** et choisissez **créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pour ce faire, dans Visual Studio 2017, choisissez **fichier > Nouveau > projet**, puis sélectionnez **Visual C# > Web > Application Web ASP.NET**. Dans la section des modèles **ASP.NET 4.5.2** , sélectionnez **MVC**. Assurez-vous que l’option **activer la prise en charge Docker** n’est pas sélectionnée et que **authentification** a la valeur **aucune authentification**. Nommez le projet **MyASPApp**.)
    ::: moniker-end

2. Ouvrez le fichier HomeController.cs et définissez un point d’arrêt dans la méthode `About()` .

## <a name="bkmk_configureIIS"></a> Installer et configurer IIS sur Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Mettre à jour les paramètres de sécurité de navigateur sur Windows Server

Si la Configuration de sécurité renforcée est activée dans Internet Explorer (il est activé par défaut), vous devrez peut-être ajouter des domaines comme sites approuvés pour vous permettre de télécharger certaines des composants de serveur web. Ajouter les sites de confiance en accédant à **Options Internet > sécurité > Sites de confiance > Sites**. Ajoutez les domaines suivants.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Lorsque vous téléchargez le logiciel, vous pouvez obtenir des demandes pour accorder des autorisations requises pour charger des différents scripts de site web et des ressources. Certaines de ces ressources ne sont pas nécessaires, mais pour simplifier le processus, cliquez sur **ajouter** lorsque vous y êtes invité.

## <a name="BKMK_deploy_asp_net"></a> Installer ASP.NET 4.5 sur Windows Server

Si vous souhaitez des informations plus détaillées pour installer ASP.NET sur IIS, consultez [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Dans le volet gauche du Gestionnaire de serveur, sélectionnez **IIS**. Cliquez avec le bouton droit sur le serveur, puis sélectionnez **Gestionnaire des services Internet (IIS)**.

1. Web Platform Installer (WebPI) permet d’installer ASP.NET 4.5 (à partir du nœud de serveur dans Windows Server 2012 R2, choisissez **obtenir nouveaux composants Web Platform** , puis recherchez ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Si vous utilisez Windows Server 2008 R2, installez ASP.NET 4 au lieu d’utiliser cette commande :

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Redémarrez le système ou exécutez **net stop was /y** suivi de **net start w3svc** à partir d’une invite de commandes pour prendre en compte une modification de la variable système PATH.

## <a name="choose-a-deployment-option"></a>Choisissez une option de déploiement

Si vous avez besoin vous aide à déployer l’application sur IIS, considérez ces options :

* Déployer en créant un fichier de paramètres de publication dans IIS et de l’importation des paramètres dans Visual Studio. Dans certains scénarios, il s’agit d’un moyen rapide pour déployer votre application. Lorsque vous créez le fichier de paramètres de publication, les autorisations sont automatiquement configurées dans IIS.

* Déployer en publiant vers un dossier local et la copie de la sortie par une méthode conseillée pour un dossier application préparée sur IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Facultatif) Déployer à l’aide d’un fichier de paramètres de publication

Vous pouvez utiliser cette option créer un fichier de paramètres de publication et l’importer dans Visual Studio.

> [!NOTE]
> Cette méthode de déploiement utilise Web Deploy. Si vous souhaitez configurer Web Deploy manuellement dans Visual Studio au lieu d’importer les paramètres, vous pouvez installer Web déployer 3.6 au lieu de 3.6 de déploiement Web pour les serveurs d’hébergement. Toutefois, si vous configurez Web Deploy manuellement, vous devez vous assurer qu’un dossier d’application sur le serveur est configuré avec les valeurs correctes et les autorisations (voir [site Web de ASP.NET configurer](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installer et configurer Web Deploy pour les serveurs d’hébergement sur Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Créer le fichier de paramètres de publication dans IIS sur Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importer les paramètres de publication dans Visual Studio et déployer

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Une fois l’application déployée, elle doit démarrer automatiquement. Si l’application ne démarre pas à partir de Visual Studio, démarrez l’application dans IIS.

1. Dans le **paramètres** boîte de dialogue, activer le débogage en cliquant sur **suivant**, choisissez un **déboguer** configuration, puis choisissez **supprimer les fichiers supplémentaires à destination** sous le **de publication des fichiers** options.

    > [!NOTE]
    > Si vous choisissez une configuration Release, vous désactivez le débogage dans le *web.config* lors de la publication de fichiers.

1. Cliquez sur **enregistrer** avant de republier l’application.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Facultatif) Déployer en le publiant sur un dossier local

Vous pouvez utiliser cette option pour déployer votre application si vous souhaitez copier l’application IIS à l’aide de Powershell, RoboCopy, ou que vous souhaitez copier manuellement les fichiers.

### <a name="BKMK_deploy_asp_net"></a> Configurer le site Web ASP.NET sur l’ordinateur Windows Server

1. Ouvrez l’Explorateur Windows et créez un dossier, **C:\Publish**, où vous allez déployer ultérieurement le projet ASP.NET.

2. Si elle n’est pas déjà ouverte, ouvrez le **Internet Information Services (IIS) Manager**. (Dans le volet gauche du Gestionnaire de serveur, sélectionnez **IIS**. Cliquez avec le bouton droit sur le serveur, puis sélectionnez **Gestionnaire des services Internet (IIS)**.)

3. Sous **connexions** dans le volet gauche, accédez à **Sites**.

4. Sélectionnez le **Site Web par défaut**, choisissez **paramètres de base**et définissez le **chemin d’accès physique** à **C:\Publish**.

5. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.

6. Définir le **Alias** champ **MyASPApp**, acceptez la valeur par défaut du Pool d’applications (**DefaultAppPool**) et définissez le **chemin d’accès physique** à  **C:\Publish**.

7. Sous **connexions**, sélectionnez **Pools d’applications**. Ouvrez **DefaultAppPool** et définissez le champ pool d’applications sur **ASP.NET v4.0** (ASP.NET 4.5 n’est pas une option pour le pool d’applications).

8. Avec le site sélectionné dans le Gestionnaire IIS, choisissez **modifier les autorisations**et assurez-vous que IUSR, IIS_IUSRS ou l’utilisateur configuré pour le Pool d’applications est un utilisateur autorisé avec des droits de lecture et exécution. Si aucun de ces utilisateurs sont présentes, ajoutez IUSR en tant qu’utilisateur disposant de droits de lecture et exécution.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publier et déployer l’application en publiant vers un dossier local à partir de Visual Studio

Vous pouvez également publier et déployer l’application avec le système de fichiers ou d’autres outils.

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

Téléchargez la version des outils à distance qui correspond à votre version de Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="BKMK_setup"></a> Configurer le débogueur distant sur Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si vous avez besoin pour ajouter des autorisations pour les utilisateurs supplémentaires, modifiez le mode d’authentification, ou le numéro de port pour le débogueur distant, consultez [configurer le débogueur distant](../debugger/remote-debugging.md#configure_msvsmon).

Pour plus d’informations sur l’exécution du débogueur distant en tant que service, consultez [exécuter le débogueur distant en tant que service](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="BKMK_attach"></a> Attachement à l’application ASP.NET à partir de l’ordinateur Visual Studio

1. Sur l’ordinateur Visual Studio, ouvrez la solution que vous essayez de déboguer (**MyASPApp** si vous suivez les étapes décrites dans cet article).
2. Dans Visual Studio, cliquez sur **Déboguer > Attacher au processus** (Ctrl + Alt + P).

    > [!TIP]
    > Dans Visual Studio 2017 et versions ultérieures, vous pouvez rattacher vers le même processus que vous avez précédemment attaché à l’aide de **Déboguer > Attacher au processus...** (Maj + Alt + P).

3. Définissez le champ qualificateur sur  **\<nom_ordinateur_distant >** et appuyez sur **entrée**.

    Vérifiez que Visual Studio ajoute le port requis pour le nom d’ordinateur, qui apparaît dans le format :  **\<nom_ordinateur_distant > : port**

    ::: moniker range=">=vs-2019"
    Dans Visual Studio 2019, vous devez voir  **\<nom_ordinateur_distant > : 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans Visual Studio 2017, vous devez voir  **\<nom_ordinateur_distant > : 4022**
    ::: moniker-end
    Le port est requis. Si vous ne voyez pas le numéro de port, vous pouvez l’ajouter manuellement.

4. Cliquez sur **Actualiser**.
    Des processus doivent s’afficher dans la fenêtre **Processus disponibles** .

    Si vous ne voyez pas tous les processus, essayez d’utiliser l’adresse IP au lieu du nom de l’ordinateur distant (le port est requis). Vous pouvez utiliser `ipconfig` dans une ligne de commande pour obtenir l’adresse IPv4.

5. Cochez  **Afficher les processus de tous les utilisateurs**.

6. Tapez la première lettre d’un nom de processus pour trouver rapidement **w3wp.exe** pour ASP.NET 4.5.

    Si vous avez plusieurs processus montrant **w3wp.exe**, vérifiez le **nom d’utilisateur** colonne. Dans certains scénarios, le **nom d’utilisateur** colonne indique le nom de pool de votre application, tel que **IIS APPPOOL\DefaultAppPool**. Si vous voyez le Pool d’applications, un moyen facile d’identifier le processus correct consiste à créer un nouveau nommé Pool d’applications pour l’instance d’application que vous souhaitez déboguer, et ensuite vous pouvez les retrouver aisément dans le **nom d’utilisateur** colonne.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Cliquez sur **Attacher**

8. Ouvrez le site web de l’ordinateur distant. Dans un navigateur, accédez à **http://\<nom_ordinateur_distant>**.

    La page web ASP.NET doit s’afficher.
9. Dans l’application ASP.NET en cours d’exécution, cliquez sur le lien vers le **sur** page.

    Le point d’arrêt doit être atteint dans Visual Studio.

## <a name="bkmk_openports"></a> Résolution des problèmes : Ouvrez les ports requis sur Windows Server

Dans la plupart des configurations, les ports requis sont ouverts par l’installation d’ASP.NET et le débogueur distant. Toutefois, vous devrez peut-être vérifier que les ports sont ouverts.

> [!NOTE]
> Sur une machine virtuelle Azure, vous devez ouvrir les ports via la [groupe de sécurité réseau](/azure/virtual-machines/windows/nsg-quickstart-portal).

Ports requis :

* 80 - requises pour IIS
::: moniker range=">=vs-2019"
* 4024 - requis pour le débogage distant à partir de Visual Studio 2019 (consultez [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) pour plus d’informations).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - requis pour le débogage distant à partir de Visual Studio 2017 (consultez [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) pour plus d’informations).
::: moniker-end
* UDP 3702 - port de détection de (facultatif) vous permet du **trouver** bouton lors de l’attachement au débogueur distant dans Visual Studio.

1. Pour ouvrir un port sur Windows Server, ouvrez le **Démarrer** menu, recherchez **pare-feu Windows avec fonctions avancées de sécurité**.

2. Puis choisissez **règles de trafic entrant > nouvelle règle > Port**. Choisissez **suivant** et sous **ports locaux spécifiques**, entrez le numéro de port, cliquez sur **suivant**, puis **autoriser la connexion**, cliquez sur Suivant, et Ajoutez le nom (**IIS**, **Web Deploy**, ou **msvsmon**) pour la règle de trafic entrant.

    Si vous souhaitez plus d’informations sur la configuration des pare-feu de Windows, consultez [configurer le pare-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Créer des règles supplémentaires pour les autres ports nécessaires.