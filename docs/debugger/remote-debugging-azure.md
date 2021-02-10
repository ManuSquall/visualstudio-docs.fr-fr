---
title: ASP.NET Core de débogage à distance sur IIS et Azure | Microsoft Docs
description: Découvrez comment installer et configurer une application Visual Studio ASP.NET Core, la déployer sur IIS à l’aide d’Azure et attacher le débogueur distant à partir de Visual Studio.
ms.custom: remotedebugging
ms.date: 05/06/2020
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 3ce27c692e96423bbec89914caeab3afd3e62ba4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947917"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio"></a>ASP.NET Core de débogage à distance sur IIS dans Azure dans Visual Studio

Ce guide explique comment installer et configurer une application Visual Studio ASP.NET Core, la déployer sur IIS à l’aide d’Azure et attacher le débogueur distant à partir de Visual Studio.

La méthode recommandée pour le débogage à distance sur Azure dépend de votre scénario :

* Pour déboguer ASP.NET Core sur Azure App Service, consultez [Déboguer des applications Azure à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-applications.md). Il s’agit de la méthode recommandée.
* Pour déboguer ASP.NET Core sur Azure App Service à l’aide de fonctionnalités de débogage plus traditionnelles, suivez les étapes de cette rubrique (voir la section [Déboguer à distance sur Azure App service](#remote_debug_azure_app_service)).

    Dans ce scénario, vous devez déployer votre application à partir de Visual Studio vers Azure, mais vous n’avez pas besoin d’installer ou de configurer manuellement IIS ou le débogueur distant (ces composants sont représentés par des lignes en pointillés), comme le montre l’illustration suivante.

    ![Diagramme montrant la relation entre Visual Studio, Azure App Service et une application ASP.NET. IIS et le débogueur distant sont représentés par des lignes en pointillés.](../debugger/media/remote-debugger-azure-app-service.png)

* Pour déboguer IIS sur une machine virtuelle Azure, suivez les étapes de cette rubrique (voir la section [débogage distant sur une machine virtuelle Azure](#remote_debug_azure_vm)). Cela vous permet d’utiliser une configuration personnalisée d’IIS, mais les étapes de configuration et de déploiement sont plus compliquées.

    Pour une machine virtuelle Azure, vous devez déployer votre application à partir de Visual Studio dans Azure, et vous devez également installer manuellement le rôle IIS et le débogueur distant, comme indiqué dans l’illustration suivante.

    ![Diagramme montrant la relation entre Visual Studio, une machine virtuelle Azure et une application ASP.NET. IIS et le débogueur distant sont représentés par des lignes pleines.](../debugger/media/remote-debugger-azure-vm.png)

* Pour déboguer des ASP.NET Core sur Service Fabric Azure, consultez [déboguer une application de service fabric à distance](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Veillez à supprimer les ressources Azure que vous créez lorsque vous avez terminé les étapes de ce didacticiel. De cette façon, vous pouvez éviter les frais inutiles.

## <a name="prerequisites"></a>Prérequis

::: moniker range=">=vs-2019"
Visual Studio 2019 est requis pour suivre les étapes décrites dans cet article.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 est requis pour suivre les étapes décrites dans cet article.
::: moniker-end

### <a name="network-requirements"></a>Configuration requise pour le réseau

Le débogage entre deux ordinateurs connectés via un proxy n’est pas pris en charge. Le débogage sur une connexion à latence élevée ou à faible bande passante, tel qu’Internet à distance ou sur Internet dans les différents pays, n’est pas recommandé et peut échouer ou être trop lent. Pour obtenir la liste complète des conditions requises, consultez [Configuration requise](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Créer l’application ASP.NET Core sur l’ordinateur Visual Studio

1. Créez une application de ASP.NET Core.

    ::: moniker range=">=vs-2019"
    Dans Visual Studio 2019, tapez **CTRL + Q** pour ouvrir la zone de recherche, tapez **ASP.net**, choisissez **modèles**, puis **créer une application Web de ASP.net Core**. Dans la boîte de dialogue qui s’affiche, nommez le projet **MyASPApp**, puis choisissez **créer**. Ensuite, choisissez **application Web (Model-View-Controller)**, puis cliquez sur **créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans Visual Studio 2017, choisissez **fichier > nouveau > projet**, puis sélectionnez **Visual C# > Web > ASP.net Core application Web**. Dans la section modèles de ASP.NET Core, sélectionnez **application Web (Model-View-Controller)**. Assurez-vous que ASP.NET Core 2,1 est sélectionné, et que l’option **activer la prise en charge** de l’ancrage n’est pas sélectionnée et que **l’authentification** est définie sur **aucune authentification**. Nommez le projet **MyASPApp**.
    ::: moniker-end

1. Ouvrez le fichier About.cshtml.cs et définissez un point d’arrêt dans la `OnGet` méthode (dans modèles plus anciens, ouvrez HomeController.cs à la place et définissez le point d’arrêt dans la `About()` méthode).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a><a name="remote_debug_azure_app_service"></a> Débogage à distance ASP.NET Core sur une Azure App Service

Dans Visual Studio, vous pouvez rapidement publier et déboguer votre application sur une instance entièrement approvisionnée d’IIS. Toutefois, la configuration d’IIS est prédéfinie et vous ne pouvez pas le personnaliser. Pour obtenir des instructions plus détaillées, consultez [déployer une application web ASP.net Core sur Azure à l’aide de Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Si vous avez besoin de personnaliser IIS, essayez de déboguer sur une [machine virtuelle Azure](#remote_debug_azure_vm).)

#### <a name="to-deploy-the-app-and-remote-debug-using-cloud-explorer"></a>Pour déployer l’application et le débogage à distance à l’aide de Cloud Explorer

1. Dans Visual Studio, cliquez avec le bouton droit sur le nœud du projet et choisissez **publier**.

    Si vous avez déjà configuré des profils de publication, le volet **Publier** s’affiche. Cliquez sur **nouveau profil**.

1. Choisissez **Azure App service** dans la boîte de dialogue **publier** , sélectionnez **créer**, puis suivez les invites pour créer un profil.

    Pour des instructions détaillées, consultez [Déployer une application web ASP.NET Core sur Azure avec Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publier sur Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Dans la fenêtre publier, choisissez **modifier la configuration** et basculez vers une configuration de débogage, puis choisissez **publier**.

   Une configuration Debug est requise pour déboguer l’application.

1. Ouvrez **Cloud Explorer** (**Afficher**  >  **Cloud Explorer**), cliquez avec le bouton droit sur l’instance de App service, puis choisissez **attacher le débogueur**.

   Si Cloud Explorer n’est pas disponible, ouvrez Explorateur de serveurs à la place. Ensuite, cliquez avec le bouton droit sur l’instance de App Service dans Explorateur de serveurs puis choisissez **attacher le débogueur**.

1. Dans l’application ASP.NET en cours d’exécution, cliquez sur le lien vers la page **à propos** de.

    Le point d’arrêt doit être atteint dans Visual Studio.

    Et voilà ! Les autres étapes de cette rubrique s’appliquent au débogage à distance sur une machine virtuelle Azure.

## <a name="remote-debug-aspnet-core-on-an-azure-vm"></a><a name="remote_debug_azure_vm"></a> Débogage à distance ASP.NET Core sur une machine virtuelle Azure

Vous pouvez créer une machine virtuelle Azure pour Windows Server, puis installer et configurer IIS et les autres composants logiciels requis. Cela prend plus de temps que le déploiement sur un Azure App Service et nécessite que vous suiviez les étapes restantes de ce didacticiel.

Ces procédures ont été testées sur ces configurations de serveur :
* Windows Server 2012 R2 et IIS 8
* Windows Server 2016 et IIS 10
* Windows Server 2019 et IIS 10

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>L’application est déjà en cours d’exécution dans IIS sur la machine virtuelle Azure ?

Cet article explique comment configurer une configuration de base d’IIS sur Windows Server et comment déployer l’application à partir de Visual Studio. Ces étapes sont incluses pour s’assurer que les composants requis sont installés sur le serveur, que l’application peut s’exécuter correctement et que vous êtes prêt à effectuer un débogage distant.

* Si votre application s’exécute dans IIS et que vous souhaitez simplement télécharger le débogueur distant et démarrer le débogage, accédez à [Télécharger et installer les outils de contrôle à distance sur Windows Server](#BKMK_msvsmon).

* Si vous souhaitez vous assurer que votre application est configurée, déployée et exécutée correctement dans IIS afin de pouvoir effectuer le débogage, suivez toutes les étapes de cette rubrique.

  * Avant de commencer, suivez toutes les étapes décrites dans [installer et exécuter IIS](/azure/virtual-machines/windows/quick-create-portal).

  * Lorsque vous ouvrez le port 80 dans le groupe de sécurité réseau, ouvrez également le [port approprié](#bkmk_openports) pour le débogueur distant (4024 ou 4022). De cette façon, vous n’aurez pas à l’ouvrir ultérieurement. Si vous utilisez Web Deploy, ouvrez également le port 8172.

### <a name="update-browser-security-settings-on-windows-server"></a>Mettre à jour les paramètres de sécurité du navigateur sur Windows Server

Si la configuration de sécurité renforcée est activée dans Internet Explorer (elle est activée par défaut), vous devrez peut-être ajouter des domaines en tant que sites approuvés pour pouvoir télécharger certains composants de serveur Web. Pour ajouter des sites de confiance, accédez à **Options Internet > sécurité > sites de confiance > sites**. Ajoutez les domaines suivants.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Lorsque vous téléchargez le logiciel, vous pouvez recevoir des demandes pour accorder l’autorisation de charger divers scripts et ressources de site Web. Certaines de ces ressources ne sont pas requises, mais pour simplifier le processus, cliquez sur **Ajouter** lorsque vous y êtes invité.

### <a name="install-aspnet-core-on-windows-server"></a>Installer ASP.NET Core sur Windows Server

1. Installez le bundle d’hébergement .NET Core sur le système hôte. Le bundle installe le Runtime .NET Core, la bibliothèque .NET Core et le Module ASP.NET Core. Pour obtenir des instructions plus détaillées, consultez [publication sur IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    Pour .NET Core 3, installez le [bundle d’hébergement .net Core](https://dotnet.microsoft.com/permalink/dotnetcore-current-windows-runtime-bundle-installer).
    Pour .NET Core 2, installez l' [hébergement .net Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting).

    > [!NOTE]
    > Si le système n’a pas de connexion Internet, obtenez et installez *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* avant d’installer le bundle d’hébergement .NET Core Windows Server.

3. Redémarrez le système ou exécutez **net stop was /y** suivi de **net start w3svc** à partir d’une invite de commandes pour prendre en compte une modification de la variable système PATH.

## <a name="choose-a-deployment-option"></a>Choisir une option de déploiement

Si vous avez besoin d’aide pour déployer l’application sur IIS, envisagez les options suivantes :

* Déployez en créant un fichier de paramètres de publication dans IIS et en important les paramètres dans Visual Studio. Dans certains scénarios, il s’agit d’un moyen rapide de déployer votre application. Lorsque vous créez le fichier de paramètres de publication, les autorisations sont automatiquement configurées dans IIS.

* Déployez en publiant dans un dossier local et en copiant la sortie par une méthode par défaut dans un dossier d’application préparé sur IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>Facultatif Déployer à l’aide d’un fichier de paramètres de publication

Vous pouvez utiliser cette option pour créer un fichier de paramètres de publication et l’importer dans Visual Studio.

> [!NOTE]
> Cette méthode de déploiement utilise Web Deploy, qui doit être installé sur le serveur. Si vous souhaitez configurer Web Deploy manuellement au lieu d’importer les paramètres, vous pouvez installer Web Deploy 3,6 au lieu de Web Deploy 3,6 pour les serveurs d’hébergement. Toutefois, si vous configurez Web Deploy manuellement, vous devez vous assurer qu’un dossier d’application sur le serveur est configuré avec les valeurs et autorisations appropriées (voir [configurer le site Web ASP.net](#BKMK_deploy_asp_net)).

### <a name="configure-the-aspnet-core-web-site"></a>Configurer le site Web ASP.NET Core

1. Dans le gestionnaire des services Internet, dans le volet gauche, sous **connexions**, sélectionnez **pools d’applications**. Ouvrez **DefaultAppPool** et définissez la **version CLR .net** sur **aucun code managé**. Cela est nécessaire pour ASP.NET Core. Le site Web par défaut utilise DefaultAppPool.

2. Arrêtez et redémarrez DefaultAppPool.

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installer et configurer Web Deploy pour les serveurs d’hébergement sur Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Créer le fichier de paramètres de publication dans IIS sur Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importer les paramètres de publication dans Visual Studio et déployer

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

> [!NOTE]
> Si vous redémarrez une machine virtuelle Azure, l’adresse IP peut changer.

Une fois l’application déployée, elle doit démarrer automatiquement. Si l’application ne démarre pas à partir de Visual Studio, démarrez l’application dans IIS pour vérifier qu’elle s’exécute correctement. Par ASP.NET Core, vous devez également vous assurer que le champ pool d’applications pour **DefaultAppPool** est défini sur **aucun code managé**.

1. Dans la boîte de dialogue **paramètres** , activez le débogage en cliquant sur **suivant**, choisissez une configuration de **débogage** , puis choisissez **Supprimer les fichiers supplémentaires à la destination** sous les options de publication de **fichier** .

    > [!IMPORTANT]
    > Si vous choisissez une configuration Release, vous désactivez le débogage dans le fichier *web.config* lors de la publication.

1. Cliquez sur **Enregistrer** , puis republiez l’application.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>Facultatif Déployer en publiant dans un dossier local

Vous pouvez utiliser cette option pour déployer votre application si vous souhaitez copier l’application sur IIS à l’aide de PowerShell, RoboCopy ou si vous souhaitez copier manuellement les fichiers.

### <a name="configure-the-aspnet-core-web-site-on-the-windows-server-computer"></a><a name="BKMK_deploy_asp_net"></a> Configurer le site Web ASP.NET Core sur l’ordinateur Windows Server

Si vous importez des paramètres de publication, vous pouvez ignorer cette section.

1. Ouvrez le **Gestionnaire des services Internet (IIS)** .et accédez à **Sites**.

2. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.

3. Définissez le champ **alias** sur **MyASPApp** et le champ pool d’applications sur **aucun code managé**. Définissez le **chemin d’accès physique** sur **C:\Publish** (où vous déploierez ultérieurement le projet ASP.net Core).

4. Avec le site sélectionné dans le gestionnaire des services Internet, sélectionnez **modifier les autorisations**, puis vérifiez que IUSR, IIS_IUSRS ou l’utilisateur configuré pour le pool d’applications est un utilisateur autorisé avec des droits lecture & exécuter.

    Si vous ne voyez pas l’un de ces utilisateurs avec un accès, passez en revue les étapes permettant d’ajouter IUSR en tant qu’utilisateur avec des droits lire & exécuter.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Facultatif Publier et déployer l’application en publiant dans un dossier local à partir de Visual Studio

Si vous n’utilisez pas Web Deploy, vous devez publier et déployer l’application à l’aide du système de fichiers ou d’autres outils. Vous pouvez commencer par créer un package à l’aide du système de fichiers, puis déployer le package manuellement ou utiliser d’autres outils tels que PowerShell, Robocopy ou XCopy. Dans cette section, nous partons du principe que vous copiez manuellement le package si vous n’utilisez pas Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a> Télécharger et installer les outils de contrôle à distance sur Windows Server

Téléchargez la version des outils de contrôle à distance qui correspond à votre version de Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a> Configurer le débogueur distant sur Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si vous devez ajouter des autorisations pour des utilisateurs supplémentaires, modifier le mode d’authentification ou le numéro de port pour le débogueur distant, consultez [configurer le débogueur distant](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a> Attachement à l’application ASP.NET à partir de l’ordinateur Visual Studio

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

    Si vous souhaitez utiliser le bouton **Rechercher** , vous devrez peut-être [ouvrir le port UDP 3702](#bkmk_openports) sur le serveur.

5. Cochez  **Afficher les processus de tous les utilisateurs**.

6. Tapez la première lettre de votre nom de processus pour trouver rapidement votre application.

    * Si vous utilisez le [modèle d’hébergement in-process](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) sur IIS, sélectionnez le processus de **w3wp.exe** approprié. À compter de .NET Core 3, il s’agit de la valeur par défaut.

    * Dans le cas contraire, sélectionnez le processus de **dotnet.exe** . (Il s’agit du modèle d’hébergement out-of-process.)

    Si vous avez plusieurs processus qui indiquent *w3wp.exe* ou *dotnet.exe*, vérifiez la colonne **nom d’utilisateur** . Dans certains scénarios, la colonne **nom d’utilisateur** affiche le nom de votre pool d’applications, par exemple **IIS APPPOOL\DefaultAppPool**. Si vous voyez le pool d’applications, mais qu’il n’est pas unique, créez un nouveau pool d’applications nommé pour l’instance d’application que vous souhaitez déboguer, puis vous pouvez le trouver facilement dans la colonne **nom d’utilisateur** .

    ::: moniker range=">=vs-2019"
    ![RemoteDBG_AttachToProcess](../debugger/media/vs-2019/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end
    ::: moniker range="vs-2017"
    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg-attachtoprocess-aspnetcore.png "RemoteDBG_AttachToProcess")
    ::: moniker-end

7. Cliquez sur **Attacher**.

8. Ouvrez le site web de l’ordinateur distant. Dans un navigateur, accédez à **http:// \<remote computer name>**.

    La page web ASP.NET doit s’afficher.
9. Dans l’application ASP.NET en cours d’exécution, cliquez sur le lien vers la page **à propos** de.

    Le point d’arrêt doit être atteint dans Visual Studio.

### <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Résolution des problèmes Ouvrez les ports requis sur Windows Server

Dans la plupart des configurations, les ports requis sont ouverts par l’installation de ASP.NET et le débogueur distant. Toutefois, si vous dépannez des problèmes de déploiement et que l’application est hébergée derrière un pare-feu, vous devrez peut-être vérifier que les ports appropriés sont ouverts.

Sur une machine virtuelle Azure, vous devez ouvrir les ports via le [groupe de sécurité réseau](/azure/virtual-machines/windows/nsg-quickstart-portal).

Ports requis :

* 80-requis pour IIS
::: moniker range=">=vs-2019"
* 4024-requis pour le débogage distant à partir de Visual Studio 2019 (pour plus d’informations, consultez [affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
::: moniker range="vs-2017"
* 4022-requis pour le débogage distant à partir de Visual Studio 2017 (pour plus d’informations, consultez [affectations de port du débogueur distant](../debugger/remote-debugger-port-assignments.md) ).
::: moniker-end
* UDP 3702-(facultatif) le port de découverte vous permet d’accéder au bouton **Rechercher** lors de l’attachement au débogueur distant dans Visual Studio.

En outre, ces ports doivent déjà être ouverts par l’installation de ASP.NET :
- 8172-(facultatif) requis pour que Web Deploy déploie l’application à partir de Visual Studio
