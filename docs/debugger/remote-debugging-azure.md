---
title: Debug à distance ASP.NET core sur l’IIS et Azure ( Microsoft Docs
ms.custom: remotedebugging
ms.date: 04/14/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 079e324f2304118c9041118c13e8ebc0cce2015c
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385506"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>Remote Debug ASP.NET Core sur l’IIS en Azure en Visual Studio

Ce guide explique comment configurer et configurer une application Visual Studio ASP.NET Core, la déployer dans l’IIS à l’aide d’Azure et joindre le débbuggeur à distance de Visual Studio.

La façon recommandée de déboiffer à distance sur Azure dépend de votre scénario :

* Pour déboiffer ASP.NET Core sur Azure App Service, voir [les applications Debug Azure à l’aide de Snapshot Debugger](../debugger/debug-live-azure-applications.md). Il s’agit de la méthode recommandée.
* Pour déboguer ASP.NET Core sur Azure App Service en utilisant des fonctionnalités de débogage plus traditionnelles, suivez les étapes de ce sujet (voir la section [Remote debug sur Azure App Service](#remote_debug_azure_app_service)).

    Dans ce scénario, vous devez déployer votre application de Visual Studio à Azure, mais vous n’avez pas besoin d’installer ou configurer manuellement IIS ou le débbugger à distance (ces composants sont représentés avec des lignes pointillées), comme indiqué dans l’illustration suivante.

    ![Composants de débbuggeurs à distance](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Pour déboquer IIS sur un VM Azure, suivez les étapes de ce sujet (voir la section [Remote Debug sur un Azure VM](#remote_debug_azure_vm)). Cela vous permet d’utiliser une configuration personnalisée de l’IIS, mais les étapes de configuration et de déploiement sont plus compliquées.

    Pour un Azure VM, vous devez déployer votre application de Visual Studio à Azure et vous devez également installer manuellement le rôle IIS et le débbuggeur à distance, comme le montre l’illustration suivante.

    ![Composants de débbuggeurs à distance](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Pour déboquer ASP.NET Core sur Azure Service Fabric, voir [Debug une application Remote Service Fabric](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Assurez-vous de supprimer les ressources Azure que vous créez lorsque vous avez terminé les étapes de ce tutoriel. De cette façon, vous pouvez éviter d’encourir des frais inutiles.

## <a name="prerequisites"></a>Prérequis

::: moniker range=">=vs-2019"
Visual Studio 2019 est tenu de suivre les étapes indiquées dans cet article.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 est tenu de suivre les étapes indiquées dans cet article.
::: moniker-end

### <a name="network-requirements"></a>Configuration requise pour le réseau

Le débogage entre deux ordinateurs connectés par un proxy n’est pas pris en charge. Il n’est pas recommandé de déracyer une latence élevée ou une faible connexion à bande passante, comme Internet commutée ou sur Internet à travers les pays, et peut échouer ou être inacceptablement lent. Pour une liste complète des exigences, voir [Exigences](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Créez l’application ASP.NET Core sur l’ordinateur Visual Studio

1. Créez une nouvelle application ASP.NET Core.

    ::: moniker range=">=vs-2019"
    Dans Visual Studio 2019, tapez **Ctrl Q** pour ouvrir la boîte de recherche, **tapez asp.net**, choisissez **Templates**, puis choisissez **Créer de nouvelles ASP.NET’application Web de base.** Dans la boîte de dialogue qui apparaît, nom du projet **MyASPApp**, puis choisissez **Create**. Ensuite, choisissez **l’application Web (Model-View-Controller)**, puis choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans Visual Studio 2017, choisissez **File > New > Project**, puis sélectionnez Visual C > Web > ASP.NET Core Web **Application**. Dans la section ASP.NET modèles de base, sélectionnez **l’application Web (Model-View-Controller)**. Assurez-vous que ASP.NET Core 2.1 est sélectionné, que **le support Enable Docker** n’est pas sélectionné et que **l’authentification** est définie **à Aucune authentification**. Nommez le projet **MyASPApp**.
    ::: moniker-end

1. Ouvrez le fichier About.cshtml.cs et définissez `OnGet` un point d’arrêt dans la méthode (dans les `About()` anciens modèles, ouvrez HomeController.cs à la place et définissez le point d’arrêt dans la méthode).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a>Remote Debug ASP.NET Core sur un service d’application Azure

De Visual Studio, vous pouvez rapidement publier et déboiffer votre application à une instance entièrement provisionnée de l’IIS. Cependant, la configuration de l’IIS est prédéfinie et vous ne pouvez pas la personnaliser. Pour des instructions plus détaillées, voir [Déployez une application web ASP.NET Core à Azure à l’aide de Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Si vous avez besoin de la possibilité de personnaliser IIS, essayez de débogage sur un [Azure VM](#remote_debug_azure_vm).)

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Pour déployer l’application et le débogé à distance à l’aide de Cloud Explorer

1. Dans Visual Studio, cliquez à droite sur le nœud du projet et choisissez **Publish**.

    Si vous avez déjà configuré des profils de publication, le volet **Publier** s’affiche. Cliquez sur **Nouveau profil**.

1. Choisissez **Azure App Service** dans la boîte de dialogue **Publish,** sélectionnez **Créer de nouveaux**et suivez les invites pour créer un profil.

    Pour des instructions détaillées, consultez [Déployer une application web ASP.NET Core sur Azure avec Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publier sur Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Dans la fenêtre Publier, choisissez **Modifier la configuration** et passez à une configuration Debug, puis choisissez **Publish**.

   Une configuration Debug est nécessaire pour déboiffer l’application.

1. Open **Cloud Explorer** (**Voir** > Cloud**Explorer**), cliquez à droite sur l’instance App Service et choisissez **Attach Debugger**.

   Si Cloud Explorer n’est pas disponible, ouvrez Server Explorer à la place. Ensuite, cliquez à droite sur l’instance App Service dans Server Explorer et choisissez **Attach Debugger**.

1. Dans l’application en cours d’exécution ASP.NET, cliquez sur le lien vers la page **About.**

    Le point d’arrêt doit être atteint dans Visual Studio.

    Et voilà ! Le reste des étapes de ce sujet s’applique au débogage à distance sur un VM Azure.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a>Debug à distance ASP.NET core sur un VM Azure

Vous pouvez créer un Azure VM pour Windows Server, puis installer et configurer IIS et les autres composants logiciels requis. Cela prend plus de temps que de déployer à un service d’application Azure et exige que vous suiviez les étapes restantes dans ce tutoriel.

Ces procédures ont été testées sur ces configurations de serveur :
* Windows Server 2012 R2 et IIS 8
* Windows Server 2016 et IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>App déjà en cours d’exécution dans l’IIS sur l’Azure VM?

Cet article comprend des étapes sur la configuration d’une configuration de base de l’IIS sur le serveur Windows et le déploiement de l’application à partir de Visual Studio. Ces étapes sont incluses pour s’assurer que le serveur a installé les composants requis, que l’application peut fonctionner correctement, et que vous êtes prêt à déboguer à distance.

* Si votre application est en cours d’exécution dans IIS et que vous voulez juste télécharger le débbugger à distance et commencer à débogage, aller à [Télécharger et installer les outils à distance sur Windows Server](#BKMK_msvsmon).

* Si vous voulez de l’aide pour vous assurer que votre application est configurée, déployée et correctement en cours d’exécution dans l’IIS afin que vous puissiez déboguer, suivez toutes les étapes de ce sujet.

  * Avant de commencer, suivez toutes les étapes décrites dans [Installer et exécuter IIS](/azure/virtual-machines/windows/quick-create-portal).

  * Lorsque vous ouvrez le port 80 dans le groupe de sécurité réseau, ouvrez également le [port correct](#bkmk_openports) pour le débbugger à distance (4024 ou 4022). De cette façon, vous n’aurez pas à l’ouvrir plus tard.

### <a name="update-browser-security-settings-on-windows-server"></a>Mettre à jour les paramètres de sécurité du navigateur sur Windows Server

Si la configuration de sécurité améliorée est activée dans Internet Explorer (elle est activée par défaut), alors vous devrez peut-être ajouter certains domaines comme sites de confiance pour vous permettre de télécharger certains des composants du serveur Web. Ajoutez les sites de confiance en vous rendant à **Internet Options > Sécurité > sites de confiance > sites**. Ajoutez les domaines suivants.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Lorsque vous téléchargez le logiciel, vous pouvez obtenir des demandes d’autorisation d’accorder la permission de charger divers scripts et ressources de site Web. Certaines de ces ressources ne sont pas nécessaires, mais pour simplifier le processus, cliquez sur **Ajouter** lorsqu’on l’incite.

### <a name="install-aspnet-core-on-windows-server"></a>Installer ASP.NET Core sur Windows Server

1. Installez le [bundle d’hébergement .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) sur le système hôte. Le bundle installe le Runtime .NET Core, la bibliothèque .NET Core et le Module ASP.NET Core. Pour des instructions plus approfondies, voir [Éditions à l’IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Si le système n’a pas de connexion Internet, obtenez et installez *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* avant d’installer le bundle d’hébergement .NET Core Windows Server.

3. Redémarrez le système ou exécutez **net stop was /y** suivi de **net start w3svc** à partir d’une invite de commandes pour prendre en compte une modification de la variable système PATH.

## <a name="choose-a-deployment-option"></a>Choisissez une option de déploiement

Si vous avez besoin d’aide pour déployer l’application à IIS, considérez ces options :

* Déployez en créant un fichier de paramètres de publication dans l’IIS et en important les paramètres de Visual Studio. Dans certains scénarios, il s’agit d’un moyen rapide de déployer votre application. Lorsque vous créez le fichier de paramètres de publication, les autorisations sont automatiquement configurés dans l’IIS.

* Déployer en publiant un dossier local et en copiant la sortie par une méthode préférée à un dossier d’application préparé sur IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Facultatif) Déploiement à l’aide d’un fichier de paramètres de publication

Vous pouvez utiliser cette option créer un fichier de paramètres de publication et l’importer dans Visual Studio.

> [!NOTE]
> Cette méthode de déploiement utilise Web Deploy. Si vous souhaitez configurer le déploiement Web manuellement dans Visual Studio au lieu d’importer les paramètres, vous pouvez installer Web Deploy 3.6 au lieu de Web Deploy 3.6 pour les serveurs d’hébergement. Toutefois, si vous configurez le déploiement Web manuellement, vous devrez vous assurer qu’un dossier d’application sur le serveur est configuré avec les valeurs et les autorisations correctes (voir [Configurer ASP.NET site Web](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installer et configurer le déploiement Web pour héberger des serveurs sur Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Créer le fichier de paramètres de publication dans IIS sur Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importer les paramètres de publication dans Visual Studio et déployer

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Une fois l’application déployée, elle doit démarrer automatiquement. Si l’application ne part pas de Visual Studio, démarrez l’application en IIS. Pour ASP.NET Core, vous devez vérifier que le champ Pool d’applications pour **DefaultAppPool** est défini sur **Aucun code managé**.

1. Dans la boîte de dialogue **Paramètres,** activez le débogage en cliquant sur **Next,** choisissez une configuration **Debug,** puis choisissez **Supprimer les fichiers supplémentaires à destination** dans le cadre des options De **Publish.**

    > [!NOTE]
    > Si vous choisissez une configuration de version, vous désactivez le débogage dans le fichier *web.config* lorsque vous publiez.

1. Cliquez **sur Enregistrer** et ensuite rééditer l’application.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Facultatif) Déployer en publiant dans un dossier local

Vous pouvez utiliser cette option pour déployer votre application si vous souhaitez copier l’application à IIS à l’aide de PowerShell, RoboCopy, ou si vous souhaitez copier manuellement les fichiers.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a>Configurer le site Web ASP.NET Core sur l’ordinateur Windows Server

Si vous importez des paramètres de publication, vous pouvez sauter cette section.

1. Ouvrez le **Gestionnaire des services Internet (IIS)** .et accédez à **Sites**.

2. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.

3. Définissez le champ **Alias** sur **MyASPApp** et le champ de piscine d’applications **sans code géré**. Définissez le **chemin physique vers** **C: 'Publier** (où vous déployez plus tard le projet ASP.NET Core).

4. Avec le site sélectionné dans le gestionnaire DE l’IIS, choisissez **Edit Permissions**, et assurez-vous que IUSR, IIS_IUSRS ou l’utilisateur configuré pour le pool d’applications est un utilisateur autorisé avec lire & les droits d’exécution.

    Si vous ne voyez pas l’un de ces utilisateurs avec accès, passez par des étapes pour ajouter IUSR en tant qu’utilisateur avec Lire & Les droits d’exécution.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Facultatif) Publier et déployer l’application en publiant dans un dossier local de Visual Studio

Si vous n’utilisez pas Web Deploy, vous devez publier et déployer l’application à l’aide du système de fichiers ou d’autres outils. Vous pouvez commencer par créer un paquet à l’aide du système de fichiers, puis soit déployer le paquet manuellement ou utiliser d’autres outils comme PowerShell, RoboCopy, ou XCopy. Dans cette section, nous supposons que vous copiez manuellement le paquet si vous n’utilisez pas Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Téléchargez et installez les outils distants sur Windows Server

Téléchargez la version des outils distants qui correspondent à votre version de Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Configurez le débbugger à distance sur Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si vous avez besoin d’ajouter des autorisations pour d’autres utilisateurs, modifier le mode d’authentification, ou le numéro de port pour le débbugger à distance, voir [Configure Configurer le débbugger à distance](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Joindre à l’application ASP.NET à partir de l’ordinateur Visual Studio

1. Sur l’ordinateur Visual Studio, ouvrez la solution que vous essayez de déboiffer (**MyASPApp** si vous suivez les étapes de cet article).
2. Dans Visual Studio, cliquez sur **Debug > Attach to Process** (Ctrl et Alt et P).

    > [!TIP]
    > Dans Visual Studio 2017 et les versions ultérieures, vous pouvez ré-attacher au même processus que vous avez précédemment attaché à en utilisant **Debug > Reattach to Process...** (Shift-Alt-P).

3. Définissez le champ de qualification à ** \<distance nom de l’ordinateur>** et appuyez **sur Enter**.

    Vérifiez que Visual Studio ajoute le port requis au nom de l’ordinateur, qui apparaît dans le format: ** \<nom d’ordinateur à distance>:port**

    ::: moniker range=">=vs-2019"
    Sur Visual Studio 2019, vous devriez voir ** \<le nom de l’ordinateur à distance>:4024**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Sur Visual Studio 2017, vous devriez voir ** \<le nom de l’ordinateur à distance>:4022**
    ::: moniker-end
    Le port est nécessaire. Si vous ne voyez pas le numéro de port, ajoutez-le manuellement.

4. Cliquez sur **Actualiser**.
    Des processus doivent s’afficher dans la fenêtre **Processus disponibles** .

    Si vous ne voyez aucun processus, essayez d’utiliser l’adresse IP au lieu du nom de l’ordinateur distant (le port est nécessaire). Vous pouvez `ipconfig` utiliser dans une ligne de commande pour obtenir l’adresse IPv4.

    Si vous souhaitez utiliser le bouton **Trouver,** vous devrez peut-être ouvrir le [port UDP 3702](#bkmk_openports) sur le serveur.

5. Cochez  **Afficher les processus de tous les utilisateurs**.

6. Tapez la première lettre de votre nom de processus pour trouver rapidement votre application.

    * Sélectionnez **dotnet.exe** (pour .NET Core)

      Si vous avez plusieurs processus montrant **dotnet.exe**, consultez la colonne **nom de l’utilisateur.** Dans certains scénarios, la colonne **Nom de l’utilisateur** affiche le nom de votre pool d’applications, comme **IIS APPPOOL-DefaultAppPool**. Si vous voyez le Pool d’applications, un moyen facile d’identifier le processus correct est de créer un nouveau pool d’applications nommé pour l’instance d’application que vous souhaitez déboiffer, puis vous pouvez le trouver facilement dans la colonne **nom de l’utilisateur.**

    * Dans certains scénarios IIS, vous pouvez trouver votre nom d’application dans la liste de processus, tels que **MyASPApp.exe**. Vous pouvez vous attacher à ce processus à la place.

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Cliquez sur **Attacher**.

8. Ouvrez le site web de l’ordinateur distant. Dans un navigateur, accédez à **http://\<nom_ordinateur_distant>**.

    La page web ASP.NET doit s’afficher.
9. Dans l’application en cours d’exécution ASP.NET, cliquez sur le lien vers la page **About.**

    Le point d’arrêt doit être atteint dans Visual Studio.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Résolution des problèmes Ouvrez les ports requis sur Windows Server

Dans la plupart des configurations, les ports requis sont ouverts par l’installation de ASP.NET et le débbugger à distance. Toutefois, si vous êtes des problèmes de déploiement de dépannage et que l’application est hébergée derrière un pare-feu, vous devrez peut-être vérifier que les ports corrects sont ouverts.

Sur un Azure VM, vous devez ouvrir des ports via le [groupe de sécurité Réseau](/azure/virtual-machines/windows/nsg-quickstart-portal).

Ports requis :

* 80 - Nécessaire pour l’IIS
::: moniker range=">=vs-2019"
* 4024 - Nécessité pour le débogage à distance de Visual Studio 2019 (voir [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) pour plus d’informations).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Nécessité d’un débogage à distance à partir de Visual Studio 2017 (voir [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) pour plus d’informations).
::: moniker-end
* UDP 3702 - (Facultatif) Le port Discovery vous permet de passer le bouton **Trouver** lors de l’attachement au débbuggeur à distance de Visual Studio.

En outre, ces ports devraient déjà être ouverts par l’installation ASP.NET :
- 8172 - (Facultatif) Nécessaire pour le déploiement web pour déployer l’application de Visual Studio
