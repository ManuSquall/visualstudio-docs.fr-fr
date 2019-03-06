---
title: ASP.NET Core sur IIS et Azure de déboguer à distance | Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: 9d1a64da1e27f5d3504608441306e820b4547539
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710823"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Débogage distant ASP.NET Core sur IIS dans Azure dans Visual Studio 2017

Ce guide explique comment paramétrer et configurer une application ASP.NET Core Visual Studio 2017, déployez-le sur IIS à l’aide d’Azure et attacher le débogueur distant à partir de Visual Studio.

La méthode recommandée pour déboguer à distance sur Azure dépend de votre scénario :

* Pour déboguer ASP.NET Core sur Azure App Service, consultez [déboguer Azure apps à l’aide du débogueur de capture instantanée](../debugger/debug-live-azure-applications.md). Il s’agit de la méthode recommandée.
* Pour déboguer ASP.NET Core sur Azure App Service à l’aide des fonctionnalités de débogage plus classiques, suivez les étapes décrites dans cette rubrique (consultez la section [déboguer à distance sur Azure App Service](#remote_debug_azure_app_service)).

    Dans ce scénario, vous devez déployer votre application à partir de Visual Studio vers Azure, mais vous n’avez pas besoin installer manuellement ou de configurer IIS ou le débogueur distant (ces composants sont représentées par des lignes pointillées), comme indiqué dans l’illustration suivante.

    ![Composants du débogueur distant](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Pour déboguer IIS sur une machine virtuelle Azure, suivez les étapes décrites dans cette rubrique (consultez la section [déboguer à distance sur une machine virtuelle Azure](#remote_debug_azure_vm)). Cela vous permet d’utiliser une configuration personnalisée d’IIS, mais les étapes de configuration et de déploiement sont plus complexes.

    Pour une machine virtuelle Azure, vous devez déployer votre application à partir de Visual Studio vers Azure et vous devez également installer manuellement le rôle IIS et le débogueur distant, comme indiqué dans l’illustration suivante.

    ![Composants du débogueur distant](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Pour déboguer ASP.NET Core sur Azure Service Fabric, consultez [déboguer une application de Service Fabric distante](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Veillez à supprimer les ressources Azure que vous créez lorsque vous avez effectué les étapes de ce didacticiel. De cette façon, que vous pouvez éviter d’encourir des frais inutiles.


### <a name="requirements"></a>Spécifications

Débogage entre deux ordinateurs connectés via un proxy n’est pas pris en charge. Débogage sur une latence élevée ou faible bande passante, telles que la numérotation Internet, ou via Internet entre les pays n’est pas recommandé et peut échouer ou être trop faibles. Pour obtenir une liste complète des exigences, consultez [exigences](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Créer l’application ASP.NET Core sur l’ordinateur Visual Studio 2017

1. Créez une nouvelle application ASP.NET Core. (Choisissez **fichier > Nouveau > projet**, puis sélectionnez **Visual C# > Web > Application Web ASP.NET Core**).

    Dans le **ASP.NET Core** section de modèles, sélectionnez **Web Application**.

2. Assurez-vous que l’option **ASP.NET Core 2.0** est sélectionnée, qui **activer la prise en charge Docker** est **pas** sélectionné et que **authentification** est défini sur **Aucune authentification**.

3. Nommez le projet **MyASPApp** et cliquez sur **OK** pour créer la solution.

4. Ouvrez le fichier About.cshtml.cs et définissez un point d’arrêt dans le `OnGet` (méthode) (dans les modèles plus anciens, open Homecontrôleur.cs au lieu de cela et définir le point d’arrêt dans le `About()` méthode).

## <a name="remote_debug_azure_app_service"></a> Débogage distant ASP.NET Core sur un Azure App Service

À partir de Visual Studio, vous pouvez rapidement publier et déboguer votre application à une instance entièrement d’IIS. Toutefois, la configuration d’IIS est prédéfinie et vous ne pouvez pas la personnaliser. Pour obtenir des instructions, consultez [déployer une application web ASP.NET Core sur Azure à l’aide de Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Si vous avez besoin de la possibilité de personnaliser IIS, essayer de déboguer un [machine virtuelle Azure](#remote_debug_azure_vm).)

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Pour déployer l’application et le débogage à distance à l’aide de l’Explorateur de serveurs

1. Dans Visual Studio, cliquez sur le nœud de projet et choisissez **publier**.

    Si vous avez déjà configuré des profils de publication, le volet **Publier** s’affiche. Cliquez sur **nouveau profil**.

1. Choisissez **Azure App Service** à partir de la **publier** boîte de dialogue, sélectionnez **créer un nouveau**et suivez les invites à publier.

    Pour des instructions détaillées, consultez [Déployer une application web ASP.NET Core sur Azure avec Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publier sur Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Ouvrez **Explorateur de serveurs** (**vue** > **Explorateur de serveurs**), avec le bouton droit sur l’instance de Service de l’application et choisissez **attacher le débogueur**.

1. Dans l’application ASP.NET en cours d’exécution, cliquez sur le lien vers le **sur** page.

    Le point d’arrêt doit être atteint dans Visual Studio.

    C’est tout ! Le reste des étapes de cette rubrique s’appliquent au débogage à distance sur une machine virtuelle Azure.

## <a name="remote_debug_azure_vm"></a> Débogage à distance ASP.NET Core sur une machine virtuelle Azure

Vous pouvez créer une machine virtuelle Azure pour Windows Server et puis installer et configurer IIS et les autres composants logiciels requis. Cela prend plus de temps qu’un déploiement dans Azure App Service et nécessite que vous suivez les étapes restantes de ce didacticiel.

Tout d’abord, suivez toutes les étapes décrites dans [installer et exécuter IIS](/azure/virtual-machines/windows/quick-create-portal).

Lorsque vous ouvrez le port 80 dans le groupe de sécurité réseau, vous devez également ouvrir le port 4022 pour le débogueur distant. De cette façon, vous ne devrez pas ouvrir ultérieurement.

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Application déjà en cours d’exécution dans IIS sur la machine virtuelle Azure ?

Cet article contient des instructions sur la configuration d’une configuration de base d’IIS sur Windows server et le déploiement de l’application à partir de Visual Studio. Ces étapes sont inclus pour vous assurer que le serveur a les composants requis installés, que l’application peut s’exécuter correctement et que vous êtes prêt à déboguer à distance.

* Si votre application s’exécute dans IIS et que vous souhaitez simplement télécharger le débogueur distant et démarrer le débogage, accédez à [télécharger et installer les outils à distance sur Windows Server](#BKMK_msvsmon).

* Si vous souhaitez une aide pour vous assurer que votre application est configurée, déployé et fonctionne correctement dans IIS afin que vous puissiez déboguer, suivez les étapes dans cette rubrique.

### <a name="update-browser-security-settings-on-windows-server"></a>Mettre à jour les paramètres de sécurité de navigateur sur Windows Server

Si la Configuration de sécurité renforcée est activée dans Internet Explorer (il est activé par défaut), vous devrez peut-être ajouter des domaines comme sites approuvés pour vous permettre de télécharger certaines des composants de serveur web. Ajouter les sites de confiance en accédant à **Options Internet > sécurité > Sites de confiance > Sites**. Ajoutez les domaines suivants.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Lorsque vous téléchargez le logiciel, vous pouvez obtenir des demandes pour accorder des autorisations requises pour charger des différents scripts de site web et des ressources. Certaines de ces ressources ne sont pas nécessaires, mais pour simplifier le processus, cliquez sur **ajouter** lorsque vous y êtes invité.

### <a name="install-aspnet-core-on-windows-server"></a>Installer ASP.NET Core sur Windows Server

1. Installez le [bundle d’hébergement .NET Core Windows Server](https://aka.ms/dotnetcore-2-windowshosting) sur le système hôte. Le bundle installe le Runtime .NET Core, la bibliothèque .NET Core et le Module ASP.NET Core. Pour plus d’instructions détaillées, consultez [publication sur IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Si le système n’a pas de connexion Internet, obtenez et installez *[Microsoft Visual C++ 2015 Redistributable](https://www.microsoft.com/download/details.aspx?id=53840)* avant d’installer le bundle d’hébergement .NET Core Windows Server.

3. Redémarrez le système ou exécutez **net stop was /y** suivi de **net start w3svc** à partir d’une invite de commandes pour prendre en compte une modification de la variable système PATH.

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

Une fois l’application déployée, elle doit démarrer automatiquement. Si l’application ne démarre pas à partir de Visual Studio, démarrez l’application dans IIS. Pour ASP.NET Core, vous devez vérifier que le champ Pool d’applications pour **DefaultAppPool** est défini sur **Aucun code managé**.

1. Dans le **paramètres** boîte de dialogue, activer le débogage en cliquant sur **suivant**, choisissez un **déboguer** configuration, puis choisissez **supprimer les fichiers supplémentaires à destination** sous le **de publication des fichiers** options.

    > [!NOTE]
    > Si vous choisissez une configuration Release, vous désactivez le débogage dans le *web.config* lors de la publication de fichiers.

1. Cliquez sur **enregistrer** avant de republier l’application.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Facultatif) Déployer en le publiant sur un dossier local

Vous pouvez utiliser cette option pour déployer votre application si vous souhaitez copier l’application IIS à l’aide de Powershell, RoboCopy, ou que vous souhaitez copier manuellement les fichiers.

### <a name="BKMK_deploy_asp_net"></a> Configurer le site Web ASP.NET sur l’ordinateur Windows Server

Si vous importez des paramètres de publication, vous pouvez ignorer cette section.

1. Ouvrez le **Gestionnaire des services Internet (IIS)** .et accédez à **Sites**.

2. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.

3. Définir le **Alias** champ **MyASPApp** et le champ pool d’applications à **aucun Code managé**. Définir le **chemin d’accès physique** à **C:\Publish** (où vous déploierez plus tard le projet ASP.NET).

4. Avec le site sélectionné dans le Gestionnaire IIS, choisissez **modifier les autorisations**et assurez-vous que IUSR, IIS_IUSRS ou l’utilisateur configuré pour le Pool d’applications est un utilisateur autorisé avec des droits de lecture et exécution.

    Si vous ne voyez pas un de ces utilisateurs avec accès, suivez les étapes pour ajouter IUSR en tant qu’utilisateur disposant de droits de lecture et exécution.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Facultatif) Publier et déployer l’application en publiant vers un dossier local à partir de Visual Studio

Si vous n’utilisez pas Web Deploy, vous devez publier et déployer l’application avec le système de fichiers ou d’autres outils. Vous pouvez commencer par créer un package en utilisant le système de fichiers, puis déployer le package manuellement ou utiliser d’autres outils tels que PowerShell, RoboCopy ou XCopy. Dans cette section, nous supposons que vous effectuez la copie manuellement le package si vous n’utilisez pas Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Téléchargez et installez les outils à distance sur Windows Server

Dans ce didacticiel, nous utilisons Visual Studio 2017.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="BKMK_setup"></a> Configurer le débogueur distant sur Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si vous avez besoin pour ajouter des autorisations pour les utilisateurs supplémentaires, modifiez le mode d’authentification, ou le numéro de port pour le débogueur distant, consultez [configurer le débogueur distant](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Attachement à l’application ASP.NET à partir de l’ordinateur Visual Studio

1. Sur l’ordinateur Visual Studio, ouvrez la solution que vous essayez de déboguer (**MyASPApp** si vous suivez les étapes décrites dans cet article).
2. Dans Visual Studio, cliquez sur **Déboguer > Attacher au processus** (Ctrl + Alt + P).

    > [!TIP]
    > Dans Visual Studio 2017, vous pouvez attacher nouveau vers le même processus que vous avez précédemment attaché à l’aide de **Déboguer > Attacher au processus...** Maj+Alt+P

3. Définissez le champ Qualificateur sur **\<nom_ordinateur_distant>:4022**.
4. Cliquez sur **Actualiser**.
    Des processus doivent s’afficher dans la fenêtre **Processus disponibles** .

    Si vous ne voyez pas tous les processus, essayez d’utiliser l’adresse IP au lieu du nom de l’ordinateur distant (le port est requis). Vous pouvez utiliser `ipconfig` dans une ligne de commande pour obtenir l’adresse IPv4.

    Si vous souhaitez utiliser le **trouver** bouton, vous devrez peut-être [ouvrir le port UDP 3702](#bkmk_openports) sur le serveur.

5. Cochez  **Afficher les processus de tous les utilisateurs**.

6. Tapez la première lettre d’un nom de processus pour trouver rapidement *dotnet.exe* (pour ASP.NET Core).

   Pour une application ASP.NET Core, le nom du processus précédent était *dnx.exe*.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Cliquez sur **Attacher**.

8. Ouvrez le site web de l’ordinateur distant. Dans un navigateur, accédez à **http://\<nom_ordinateur_distant>**.

    La page web ASP.NET doit s’afficher.
9. Dans l’application ASP.NET en cours d’exécution, cliquez sur le lien vers le **sur** page.

    Le point d’arrêt doit être atteint dans Visual Studio.

### <a name="bkmk_openports"></a> Résolution des problèmes Ouvrez les ports requis sur Windows Server

Dans la plupart des configurations, les ports requis sont ouverts par l’installation d’ASP.NET et le débogueur distant. Toutefois, si vous dépannez les problèmes de déploiement et l’application est hébergée derrière un pare-feu, vous devez vérifier que les ports appropriés sont ouverts.

Sur une machine virtuelle Azure, vous devez ouvrir les ports via la [groupe de sécurité réseau](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80-for-web-traffic).

Ports requis :

- 80 - requises pour IIS
- 4022 - requis pour le débogage distant à partir de Visual Studio 2017 (consultez [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) pour plus d’informations).
- UDP 3702 - port de détection de (facultatif) vous permet du **trouver** bouton lors de l’attachement au débogueur distant dans Visual Studio.

En outre, ces ports doivent déjà être ouvert par l’installation d’ASP.NET :
- 8172 - (facultatif) nécessaire pour Web Deploy pour déployer l’application à partir de Visual Studio
