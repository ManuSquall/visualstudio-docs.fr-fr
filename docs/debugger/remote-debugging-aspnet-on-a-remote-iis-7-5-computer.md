---
title: Déboguer à distance ASP.NET sur un ordinateur IIS
description: Découvrez comment installer et configurer une application Visual Studio ASP.NET MVC 4.5.2, la déployer sur IIS et attacher le débogueur distant à partir de Visual Studio.
ms.custom:
- remotedebugging
- seodec18
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 8a3520220da15ef771c8cecbd7962e4448727910
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815709"
---
# <a name="remote-debug-aspnet-on-a-remote-iis-computer"></a>Déboguer à distance ASP.NET sur un ordinateur distant IIS
Pour déboguer une application ASP.NET qui a été déployée sur IIS, installez et exécutez les outils de contrôle à distance sur l’ordinateur sur lequel vous avez déployé votre application, puis attachez-la à votre application en cours d’exécution à partir de Visual Studio.

![Composants du débogueur distant](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Ce guide explique comment installer et configurer une application Visual Studio ASP.NET MVC 4.5.2, la déployer sur IIS et attacher le débogueur distant à partir de Visual Studio.

> [!NOTE]
> Pour déboguer à distance ASP.NET Core à la place, consultez [débogage à distance ASP.net Core sur un ordinateur IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md). Par Azure App Service, vous pouvez facilement déployer et déboguer sur une instance préconfigurée d’IIS à l’aide des [débogueur de capture instantanée](../debugger/debug-live-azure-applications.md) (.net 4.6.1 requis) ou en [attachant le débogueur à partir de Explorateur de serveurs](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Prérequis

::: moniker range=">=vs-2019"
Visual Studio 2019 est requis pour suivre les étapes décrites dans cet article.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 est requis pour suivre les étapes décrites dans cet article.
::: moniker-end

Ces procédures ont été testées sur ces configurations de serveur :
* Windows Server 2012 R2 et IIS 8 (pour Windows Server 2008 R2, les étapes de serveur sont différentes)

## <a name="network-requirements"></a>Configuration requise pour le réseau

Le débogueur distant est pris en charge sur Windows Server à partir de Windows Server 2008 Service Pack 2. Pour obtenir la liste complète des conditions requises, consultez [Configuration requise](../debugger/remote-debugging.md#requirements_msvsmon).

> [!NOTE]
> Le débogage entre deux ordinateurs connectés via un proxy n’est pas pris en charge. Le débogage sur une connexion à latence élevée ou à faible bande passante, tel qu’Internet à distance ou sur Internet dans les différents pays, n’est pas recommandé et peut échouer ou être trop lent.

## <a name="app-already-running-in-iis"></a>L’application est déjà en cours d’exécution dans IIS ?

Cet article explique comment configurer une configuration de base d’IIS sur Windows Server et comment déployer l’application à partir de Visual Studio. Ces étapes sont incluses pour s’assurer que les composants requis sont installés sur le serveur, que l’application peut s’exécuter correctement et que vous êtes prêt à effectuer un débogage distant.

* Si votre application s’exécute dans IIS et que vous souhaitez simplement télécharger le débogueur distant et démarrer le débogage, accédez à [Télécharger et installer les outils de contrôle à distance sur Windows Server](#BKMK_msvsmon).

* Si vous souhaitez vous assurer que votre application est configurée, déployée et exécutée correctement dans IIS afin de pouvoir effectuer le débogage, suivez toutes les étapes de cette rubrique.

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Créer l’application ASP.NET 4.5.2 sur l’ordinateur Visual Studio

1. Créez une application ASP.NET MVC.

    ::: moniker range=">=vs-2019"
    Dans Visual Studio 2019, tapez **CTRL + Q** pour ouvrir la zone de recherche, tapez **ASP.net**, choisissez **modèles**, puis **créer une nouvelle application Web ASP.net (.NET Framework)**. Dans la boîte de dialogue qui s’affiche, nommez le projet **MyASPApp**, puis choisissez **créer**. Sélectionnez **MVC** et choisissez **créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Pour effectuer cette opération dans Visual Studio 2017, choisissez **fichier > nouveau > projet**, puis sélectionnez **Visual C# > Web > application Web ASP.net**. Dans la section des modèles **ASP.NET 4.5.2** , sélectionnez **MVC**. Assurez-vous que l’option **activer la prise en charge** de l’ancrage n’est pas sélectionnée et que **l’authentification** est définie sur **aucune authentification**. Nommez le projet **MyASPApp**.)
    ::: moniker-end

2. Ouvrez le fichier  *HomeController.cs* et définissez un point d’arrêt dans la `About()` méthode.

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a> Installer et configurer IIS sur Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Mettre à jour les paramètres de sécurité du navigateur sur Windows Server

Si la configuration de sécurité renforcée est activée dans Internet Explorer (elle est activée par défaut), vous devrez peut-être ajouter des domaines en tant que sites approuvés pour pouvoir télécharger certains composants de serveur Web. Pour ajouter des sites de confiance, accédez à **Options Internet > sécurité > sites de confiance > sites**. Ajoutez les domaines suivants.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Lorsque vous téléchargez le logiciel, vous pouvez recevoir des demandes pour accorder l’autorisation de charger divers scripts et ressources de site Web. Certaines de ces ressources ne sont pas requises, mais pour simplifier le processus, cliquez sur **Ajouter** lorsque vous y êtes invité.

## <a name="install-aspnet-45-on-windows-server"></a><a name="BKMK_deploy_asp_net"></a> Installer ASP.NET 4,5 sur Windows Server

Si vous souhaitez des informations plus détaillées sur l’installation de ASP.NET sur IIS, consultez [iis 8,0 avec ASP.NET 3,5 et ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Dans le volet gauche de Gestionnaire de serveur, sélectionnez **IIS**. Cliquez avec le bouton droit sur le serveur, puis sélectionnez **Gestionnaire des services Internet (IIS)**.

1. Utilisez la Web Platform Installer (WebPI) pour installer ASP.NET 4,5 (à partir du nœud du serveur dans Windows Server 2012 R2, choisissez **obtenir de nouveaux composants de la plateforme Web** , puis recherchez ASP.net).

    ![Capture d’écran de la Web Platform Installer 5,0 montrant les résultats de la recherche pour asp.net avec le composant Web Platform Component IIS : ASP.NET 4,5 entouré en rouge.](../debugger/media/remotedbg_iis_aspnet_45.png)

    > [!NOTE]
    > Si vous utilisez Windows Server 2008 R2, installez ASP.NET 4 à la place à l’aide de cette commande :

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Redémarrez le système ou exécutez **net stop was /y** suivi de **net start w3svc** à partir d’une invite de commandes pour prendre en compte une modification de la variable système PATH.

## <a name="choose-a-deployment-option"></a>Choisir une option de déploiement

Si vous avez besoin d’aide pour déployer l’application sur IIS, envisagez les options suivantes :

* Déployez en créant un fichier de paramètres de publication dans IIS et en important les paramètres dans Visual Studio. Dans certains scénarios, il s’agit d’un moyen rapide de déployer votre application. Lorsque vous créez le fichier de paramètres de publication, les autorisations sont automatiquement configurées dans IIS.

* Déployez en publiant dans un dossier local et en copiant la sortie par une méthode par défaut dans un dossier d’application préparé sur IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Facultatif Déployer à l’aide d’un fichier de paramètres de publication

Vous pouvez utiliser cette option pour créer un fichier de paramètres de publication et l’importer dans Visual Studio.

> [!NOTE]
> Cette méthode de déploiement utilise Web Deploy, qui doit être installé sur le serveur. Si vous souhaitez configurer Web Deploy manuellement au lieu d’importer les paramètres, vous pouvez installer Web Deploy 3,6 au lieu de Web Deploy 3,6 pour les serveurs d’hébergement. Toutefois, si vous configurez Web Deploy manuellement, vous devez vous assurer qu’un dossier d’application sur le serveur est configuré avec les valeurs et autorisations appropriées (voir [configurer le site Web ASP.net](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installer et configurer Web Deploy pour les serveurs d’hébergement sur Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Créer le fichier de paramètres de publication dans IIS sur Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importer les paramètres de publication dans Visual Studio et déployer

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Une fois l’application déployée, elle doit démarrer automatiquement. Si l’application ne démarre pas à partir de Visual Studio, démarrez l’application dans IIS.

1. Dans la boîte de dialogue **paramètres** , activez le débogage en cliquant sur **suivant**, choisissez une configuration de **débogage** , puis choisissez **Supprimer les fichiers supplémentaires à la destination** sous les options de publication de **fichier** .

    > [!IMPORTANT]
    > Si vous choisissez une configuration Release, vous désactivez le débogage dans le fichier *web.config* lors de la publication.

1. Cliquez sur **Enregistrer** , puis republiez l’application.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Facultatif Déployer en publiant dans un dossier local

Vous pouvez utiliser cette option pour déployer votre application si vous souhaitez copier l’application sur IIS à l’aide de PowerShell, RoboCopy ou si vous souhaitez copier manuellement les fichiers.

### <a name="configure-the-aspnet-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Configurer le site Web ASP.NET sur l’ordinateur Windows Server

1. Ouvrez l’Explorateur Windows et créez un nouveau dossier, **C:\Publish**, où vous déploierez ultérieurement le projet ASP.net.

2. S’il n’est pas déjà ouvert, ouvrez le **Gestionnaire de Internet Information Services (IIS)**. (Dans le volet gauche de Gestionnaire de serveur, sélectionnez **IIS**. Cliquez avec le bouton droit sur le serveur, puis sélectionnez **Gestionnaire de Internet Information Services (IIS)**.)

3. Sous **connexions** dans le volet gauche, accédez à **sites**.

4. Sélectionnez le **site Web par défaut**, choisissez **paramètres de base**, puis définissez le **chemin d’accès physique** sur **C:\Publish**.

5. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.

6. Définissez le champ **alias** sur **MyASPApp**, acceptez le pool d’applications par défaut (**DefaultAppPool**) et définissez le **chemin d’accès physique** sur **C:\Publish**.

7. Sous **connexions**, sélectionnez **pools d’applications**. Ouvrez **DefaultAppPool** et définissez le champ pool d’applications sur **ASP.net v 4.0** (ASP.net 4,5 n’est pas une option pour le pool d’applications).

8. Avec le site sélectionné dans le gestionnaire des services Internet, sélectionnez **modifier les autorisations**, puis vérifiez que IUSR, IIS_IUSRS ou l’utilisateur configuré pour le pool d’applications est un utilisateur autorisé avec des droits lecture & exécuter. Si aucun de ces utilisateurs n’est présent, ajoutez IUSR en tant qu’utilisateur avec des droits lire & exécuter.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publier et déployer l’application en publiant dans un dossier local à partir de Visual Studio

Vous pouvez également publier et déployer l’application à l’aide du système de fichiers ou d’autres outils.

1. (ASP.NET 4.5.2) Assurez-vous que le fichier web.config répertorie la version correcte de .NET.  Par exemple, si vous ciblez ASP.NET 4.5.2, assurez-vous que cette version est répertoriée dans web.config.

    ```xml
    <system.web>
      <compilation debug="true" targetFramework="4.5.2" />
      <httpRuntime targetFramework="4.5.2" />
      <httpModules>
        <add name="ApplicationInsightsWebTracking" type="Microsoft.ApplicationInsights.Web.ApplicationInsightsHttpModule, Microsoft.AI.Web" />
      </httpModules>
    </system.web>

    ```

    Par exemple, la version doit être 4,0 si vous installez ASP.NET 4 au lieu de 4.5.2.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Télécharger et installer les outils de contrôle à distance sur Windows Server

Téléchargez la version des outils de contrôle à distance qui correspond à votre version de Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Configurer le débogueur distant sur Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si vous devez ajouter des autorisations pour des utilisateurs supplémentaires, modifier le mode d’authentification ou le numéro de port pour le débogueur distant, consultez [configurer le débogueur distant](../debugger/remote-debugging.md#configure_msvsmon).

Pour plus d’informations sur l’exécution du débogueur distant en tant que service, consultez [exécuter le débogueur distant en tant que service](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Attachement à l’application ASP.NET à partir de l’ordinateur Visual Studio

1. Sur l’ordinateur Visual Studio, ouvrez la solution que vous essayez de déboguer (**MyASPApp** si vous suivez les étapes décrites dans cet article).
2. Dans Visual Studio, cliquez sur **Déboguer > attacher au processus** (Ctrl + Alt + P).

    > [!TIP]
    > Dans Visual Studio 2017 et versions ultérieures, vous pouvez rattacher le processus que vous avez précédemment attaché en utilisant **Déboguer > rattacher au processus...** (Maj + Alt + P).

3. Définissez le champ Qualificateur sur **\<remote computer name>** et appuyez sur **entrée**.

    Vérifiez que Visual Studio ajoute le port requis au nom de l’ordinateur, qui apparaît au format suivant : **\<remote computer name> :p Trier**

    ::: moniker range=">=vs-2019"
    Dans Visual Studio 2019, vous devez voir **\<remote computer name> : 4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans Visual Studio 2017, vous devez voir **\<remote computer name> : 4022**
    ::: moniker-end
    Le port est obligatoire. Si vous ne voyez pas le numéro de port, ajoutez-le manuellement.

4. Cliquez sur **Actualiser**.
    Des processus doivent s’afficher dans la fenêtre **Processus disponibles** .

    Si vous ne voyez aucun processus, essayez d’utiliser l’adresse IP à la place du nom de l’ordinateur distant (le port est obligatoire). Vous pouvez utiliser `ipconfig` dans une ligne de commande pour obtenir l’adresse IPv4.

5. Cochez  **Afficher les processus de tous les utilisateurs**.

6. Tapez la première lettre d’un nom de processus pour trouver rapidement **w3wp.exe** pour ASP.net 4,5.

    Si plusieurs processus indiquent **w3wp.exe**, vérifiez la colonne **nom d’utilisateur** . Dans certains scénarios, la colonne **nom d’utilisateur** affiche le nom de votre pool d’applications, par exemple **IIS APPPOOL\DefaultAppPool**. Si vous voyez le pool d’applications, un moyen simple d’identifier le processus correct consiste à créer un nouveau pool d’applications nommé pour l’instance d’application que vous souhaitez déboguer, puis vous pouvez le trouver facilement dans la colonne **nom d’utilisateur** .

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Cliquez sur **attacher**

8. Ouvrez le site web de l’ordinateur distant. Dans un navigateur, accédez à **http:// \<remote computer name>**.

    La page web ASP.NET doit s’afficher.
9. Dans l’application ASP.NET en cours d’exécution, cliquez sur le lien vers la page **à propos** de.

    Le point d’arrêt doit être atteint dans Visual Studio.

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Résolution des problèmes Ouvrez les ports requis sur Windows Server

Dans la plupart des configurations, les ports requis sont ouverts par l’installation de ASP.NET et le débogueur distant. Toutefois, vous devrez peut-être vérifier que les ports sont ouverts.

> [!NOTE]
> Sur une machine virtuelle Azure, vous devez ouvrir les ports via le [groupe de sécurité réseau](/azure/virtual-machines/windows/nsg-quickstart-portal).

Ports requis :

* 80-requis pour IIS
::: moniker range=">=vs-2019"
* 4024-requis pour le débogage distant à partir de Visual Studio 2019 (pour plus d’informations, consultez [affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
::: moniker range="vs-2017"
* 4022-requis pour le débogage distant à partir de Visual Studio 2017 (pour plus d’informations, consultez [affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
* UDP 3702-(facultatif) le port de découverte vous permet d’accéder au bouton **Rechercher** lors de l’attachement au débogueur distant dans Visual Studio.

1. Pour ouvrir un port sur Windows Server, ouvrez le menu **Démarrer** , puis recherchez **pare-feu Windows avec fonctions avancées de sécurité**.

2. Choisissez ensuite les **règles de trafic entrant > nouvelle règle > port**. Choisissez **suivant** et, sous **ports locaux spécifiques**, entrez le numéro de port, cliquez sur **suivant**, puis sur **autoriser la connexion**, cliquez sur suivant, puis ajoutez le nom (**IIS**, **Web Deploy** ou **msvsmon**) pour la règle de trafic entrant.

    Si vous souhaitez plus d’informations sur la configuration du pare-feu Windows, consultez [configurer le pare-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Créez des règles supplémentaires pour les autres ports requis.