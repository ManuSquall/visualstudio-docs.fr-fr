---
title: À distance déboguer des noyaux de ASP.NET sur IIS et Azure | Documents Microsoft
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
- dotnetcore
- azure
ms.openlocfilehash: a4e03f9a369959a5736d7030a1dac885771d7984
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746765"
---
# <a name="remote-debug-aspnet-core-on-iis-in-azure-in-visual-studio-2017"></a>Débogage distant ASP.NET Core sur IIS dans Azure dans Visual Studio 2017

Ce guide explique comment installer et configurer une application Visual Studio 2017 ASP.NET Core, déployez-le sur IIS à l’aide d’Azure et attacher le débogueur distant à partir de Visual Studio.

La méthode recommandée pour le débogage distant sur Azure dépend de votre scénario :

* Pour déboguer des noyaux de ASP.NET sur Azure App Service, consultez [Azure de déboguer les applications à l’aide du débogueur de l’instantané](../debugger/debug-live-azure-applications.md). Il s’agit de la méthode recommandée.
* Pour déboguer des noyaux ASP.NET sur Azure App Service à l’aide des fonctionnalités de débogage plus classiques, suivez les étapes décrites dans cette rubrique (consultez la section [de débogage à distance sur Azure App Service](#remote_debug_azure_app_service)).

    Dans ce scénario, vous devez déployer votre application à partir de Visual Studio vers Azure, mais vous n’avez pas besoin d’installez manuellement ou configurer les services IIS ou le débogueur distant (ces composants sont représentées par des lignes pointillées), comme indiqué dans l’illustration suivante.

    ![Composants du débogueur distant](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

* Pour déboguer IIS sur une machine virtuelle Azure, suivez les étapes décrites dans cette rubrique (consultez la section [déboguer à distance sur une machine virtuelle Azure](#remote_debug_azure_vm)). Cela vous permet d’utiliser une configuration personnalisée d’IIS, mais les étapes de configuration et de déploiement sont plus complexes.

    Pour une machine virtuelle Azure, vous devez déployer votre application à partir de Visual Studio vers Azure, et vous devez également installer manuellement le rôle IIS et le débogueur distant, comme indiqué dans l’illustration suivante.

    ![Composants du débogueur distant](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

* Pour déboguer des noyaux de ASP.NET sur Azure Service Fabric, consultez [déboguer une application de Service Fabric distante](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

> [!WARNING]
> Veillez à supprimer les ressources Azure que vous créez lorsque vous avez effectué les étapes de ce didacticiel. De cette façon, que vous pouvez éviter d’encourir de frais inutiles.


### <a name="requirements"></a>Configuration requise

Débogage entre deux ordinateurs connectés via un proxy n’est pas pris en charge. Débogage sur une latence élevée ou d’une connexion à faible bande passante, telles que les connexions à distance d’Internet, ou via Internet entre des pays n’est pas recommandé et peut échouer ou être trop faibles. Pour obtenir une liste complète des conditions requises, consultez [exigences](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Créer l’application ASP.NET Core sur l’ordinateur Visual Studio 2017 

1. Créez une application ASP.NET Core. (Choisissez **fichier > Nouveau > projet**, puis sélectionnez **Visual c# > Web > Application ASP.NET Core Web**).

    Dans le **ASP.NET Core** section modèles, sélectionnez **Application Web**.

2. Assurez-vous que **ASP.NET Core 2.0** est sélectionnée, qui **activer la prise en charge Docker** est **pas** sélectionné et que **authentification** a la valeur **Aucune authentification**.

3. Nommez le projet **MyASPApp** et cliquez sur **OK** pour créer la nouvelle solution.

4. Ouvrez le fichier About.cshtml.cs et définir un point d’arrêt dans le `OnGet` (méthode) (dans les modèles plus anciens, ouvrez plutôt HomeController.cs et définissez le point d’arrêt le `About()` méthode).

## <a name="remote_debug_azure_app_service"></a> Débogage distant ASP.NET Core sur un Service d’application Azure

À partir de Visual Studio, vous pouvez rapidement publier et déboguer votre application à une instance entièrement d’IIS. Toutefois, la configuration d’IIS est prédéfinie et vous ne pouvez pas personnaliser. Pour plus d’instructions, consultez [déployer une application de web ASP.NET Core pour Azure à l’aide de Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Si vous avez besoin de la possibilité de personnaliser IIS, essayer de déboguer un [Azure VM](#BKMK_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug-using-server-explorer"></a>Pour déployer l’application et le débogage distant à l’aide de l’Explorateur de serveurs

1. Dans Visual Studio, cliquez sur le nœud du projet et choisissez **publier**.

    Si vous avez déjà configuré des profils de publication, le **publier** volet s’affiche. Cliquez sur **nouveau profil**.

1. Choisissez **Azure App Service** à partir de la **publier** boîte de dialogue, sélectionnez **créer un nouveau**et suivez les invites à publier.

    Pour obtenir des instructions détaillées, consultez [déployer une application de web ASP.NET Core pour Azure à l’aide de Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

    ![Publier sur Azure App Service](../debugger/media/remotedbg_azure_app_service_profile.png)

1. Ouvrez **l’Explorateur de serveurs** (**vue** > **l’Explorateur de serveurs**), avec le bouton droit sur l’instance de Service de l’application et choisissez **attacher le débogueur**.

1. Dans l’application ASP.NET en cours d’exécution, cliquez sur le lien vers le **sur** page.

    Le point d’arrêt doit être atteint dans Visual Studio.

    C’est tout ! Le reste des étapes de cette rubrique s’appliquent au débogage distant sur une machine virtuelle Azure.

## <a name="remote_debug_azure_vm"></a> Débogage distant ASP.NET Core sur une machine virtuelle Azure

Vous pouvez créer une machine virtuelle Azure pour Windows Server et puis installer et configurer IIS et les autres composants logiciels requis. Cela prend plus de temps que le déploiement à un Service d’application Azure et requiert que vous suivez les étapes restantes dans ce didacticiel.

Tout d’abord, suivez toutes les étapes décrites dans [installer et exécuter IIS](/azure/virtual-machines/windows/quick-create-portal).

Lorsque vous ouvrez le port 80 dans le groupe de sécurité réseau, vous devez également ouvrir le port 4022 pour le débogueur distant. De cette façon, vous ne devez ouvrir ultérieurement.

### <a name="app-already-running-in-iis-on-the-azure-vm"></a>Application déjà en cours d’exécution dans IIS sur la machine virtuelle Azure ?

Cet article inclut les étapes de configuration de la configuration de base d’IIS sur Windows server et le déploiement de l’application à partir de Visual Studio. Ces étapes sont inclus pour vous assurer que le serveur dispose des composants requis installés, que l’application peut s’exécuter correctement et que vous êtes prêt à déboguer à distance.

* Si votre application s’exécute dans IIS et que vous souhaitez simplement télécharger le débogueur distant, démarrez le débogage, accédez à [télécharger et installer les outils à distance sur Windows Server](#BKMK_msvsmon).

* Si vous souhaitez une aide pour vous assurer que votre application est configurée, déployé et fonctionne correctement dans IIS afin que vous puissiez déboguer, suivez les étapes de cette rubrique.

### <a name="update-browser-security-settings-on-windows-server"></a>Mettre à jour les paramètres de sécurité de navigateur sur Windows Server

Si la Configuration de sécurité renforcée est activée dans Internet Explorer (elle est activée par défaut), vous devez ajouter des domaines en tant que sites de confiance pour vous permettre de télécharger des composants de serveur web. Ajouter les sites de confiance en accédant à **Options Internet > sécurité > Sites de confiance > Sites**. Ajoutez les domaines suivants.

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Lorsque vous téléchargez le logiciel, vous pouvez obtenir des demandes pour accorder des autorisations requises pour charger les différents scripts de site web et des ressources. Certaines de ces ressources ne sont pas obligatoires, mais pour simplifier le processus, cliquez sur **ajouter** lorsque vous y êtes invité.

### <a name="install-aspnet-core-on-windows-server"></a>Installez ASP.NET Core sur Windows Server

1. Installer le [hébergement sur serveur Windows .NET Core](https://aka.ms/dotnetcore-2-windowshosting) offre groupée sur le système hôte. Le groupe va installer le .NET Core Runtime, bibliothèque principale de .NET et le Module de base ASP.NET. Pour obtenir des instructions plus détaillées, consultez [publication sur IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Si le système ne dispose d’une connexion Internet, obtenez et installez le *[redistribuable Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=53840)* avant d’installer l’application d’hébergement sur serveur Windows .NET Core.

3. Redémarrer le système (ou exécutez **net stop a été /y** suivie **net démarrer w3svc** à partir d’une invite de commandes pour voir une modification dans le chemin d’accès du système).

## <a name="choose-a-deployment-option"></a>Choisissez une option de déploiement

Si vous avez besoin vous aide à déployer l’application sur IIS, considérez ces options :

* Déployer à la création d’un fichier de paramètres de publication dans IIS et l’importation des paramètres dans Visual Studio. Dans certains scénarios, il s’agit d’un moyen rapide pour déployer votre application. Lorsque vous créez le fichier de paramètres de publication, les autorisations sont automatiquement définies dans IIS.

* Déployer en publiant dans un dossier local et copie la sortie par une méthode conseillée dans un dossier d’application préparée sur IIS.

## <a name="optional-deploy-using-a-publish-settings-file"></a>(Facultatif) Déployer à l’aide d’un fichier de paramètres de publication

Vous pouvez utiliser cette option créer un fichier de paramètres de publication et l’importer dans Visual Studio.

> [!NOTE]
> Cette méthode de déploiement utilise Web Deploy. Si vous souhaitez configurer Web Deploy manuellement dans Visual Studio au lieu d’importer les paramètres, vous pouvez installer 3.6 de déploiement Web au lieu de 3.6 de déploiement Web pour les serveurs d’hébergement. Toutefois, si vous configurez Web Deploy manuellement, vous devez vous assurer qu’un dossier d’application sur le serveur est configuré avec les valeurs correctes et les autorisations (voir [site Web de ASP.NET configurer](#BKMK_deploy_asp_net)).

### <a name="install-and-configure-web-deploy-for-hosting-servers-on-windows-server"></a>Installer et configurer Web Deploy pour les serveurs d’hébergement sur Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

### <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Créer le fichier de paramètres de publication dans IIS sur Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

### <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importer les paramètres de publication dans Visual Studio et déployer

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Après que l’application a été déployé avec succès, il doit démarrer automatiquement. Si l’application ne démarre pas à partir de Visual Studio, démarrez l’application dans IIS. Pour ASP.NET Core, vous devez vous assurer que le pool d’applications de champ pour le **DefaultAppPool** a la valeur **aucun Code managé**.

1. Dans le **paramètres** boîte de dialogue, activer le débogage en cliquant sur **suivant**, choisissez un **déboguer** configuration, puis choisissez **supprimer d’autres fichiers destination** sous le **fichier publier** options.

    > [!NOTE]
    > Si vous choisissez une configuration Release, vous désactivez le débogage dans le *web.config* lors de la publication de fichiers.

1. Cliquez sur **enregistrer** et puis republier l’application.

## <a name="optional-deploy-by-publishing-to-a-local-folder"></a>(Facultatif) Déployer à la publication vers un dossier local

Vous pouvez utiliser cette option pour déployer votre application si vous souhaitez copier l’application à IIS à l’aide de Powershell, RoboCopy, ou si vous souhaitez copier manuellement les fichiers.

### <a name="BKMK_deploy_asp_net"></a> Configurer le site Web ASP.NET sur l’ordinateur Windows Server

Si vous importez des paramètres de publication, vous pouvez ignorer cette section.

1. Ouvrez le **Gestionnaire des services Internet (IIS)** .et accédez à **Sites**.

2. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.

3. Définir le **Alias** au champ **MyASPApp** et le champ pool d’applications pour **aucun Code managé**. Définir le **chemin d’accès physique** à **C:\Publish** (où vous déploierez plus tard le projet ASP.NET).

4. Le site sélectionné dans le Gestionnaire des services Internet, choisissez **modifier les autorisations**et assurez-vous que IUSR, IIS_IUSRS ou l’utilisateur configuré pour le Pool d’applications est un utilisateur autorisé avec des droits de lecture et exécution.

    Si vous ne voyez pas un de ces utilisateurs avec accès, suivez les étapes pour ajouter IUSR en tant qu’utilisateur avec des droits de lecture et exécution.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Facultatif) Publier et déployer l’application en publiant dans un dossier local à partir de Visual Studio

Si vous n’utilisez pas Web Deploy, vous devez publier et déployer l’application à l’aide du système de fichiers ou d’autres outils. Vous pouvez commencer par créer un package en utilisant le système de fichiers, puis déployer le package manuellement ou utiliser d’autres outils comme XCopy, RoboCopy ou PowerShell. Dans cette section, nous supposons que vous effectuez la copie manuellement le package si vous n’utilisez pas Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a> Téléchargez et installez les outils à distance sur Windows Server

Dans ce didacticiel, nous utilisons Visual Studio 2017.

Si vous avez des difficultés à ouvrir la page avec le téléchargement du débogueur distant, consultez [débloquer le téléchargement du fichier](../debugger/remote-debugging.md#unblock_msvsmon) de l’aide.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a> Configurer le débogueur distant sur Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si vous devez ajouter des autorisations pour les utilisateurs supplémentaires, modifier le mode d’authentification ou numéro de port pour le débogueur distant, consultez [configurer le débogueur distant](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Attachement à l’application ASP.NET à partir de l’ordinateur Visual Studio

1. Sur l’ordinateur Visual Studio, ouvrez la solution que vous essayez de déboguer (**MyASPApp** si vous suivez les étapes décrites dans cet article).
2. Dans Visual Studio, cliquez sur **Déboguer > Attacher au processus** (Ctrl + Alt + P).

    > [!TIP]
    > Dans Visual Studio 2017, vous pouvez attacher au nouveau pour le même processus que vous précédemment attaché à l’aide de **Déboguer > rattacher à un processus en cours...** (Maj + Alt + P). 

3. Définissez le champ qualificateur sur  **\<nom_ordinateur_distant > : 4022**.
4. Cliquez sur **Actualiser**.
    Des processus doivent s’afficher dans la fenêtre **Processus disponibles** .

    Si vous ne voyez pas tous les processus, essayez d’utiliser l’adresse IP au lieu du nom de l’ordinateur distant (le port est requis). Vous pouvez utiliser `ipconfig` dans une ligne de commande pour obtenir l’adresse IPv4.

    Si vous souhaitez utiliser le **trouver** bouton, vous devrez peut-être [ouvrir le port UDP 3702](#bkmk_openports) sur le serveur.

5. Cochez  **Afficher les processus de tous les utilisateurs**.

6. Tapez la première lettre d’un nom de processus pour rechercher rapidement *dotnet.exe* (pour ASP.NET Core).
   
   Pour une application ASP.NET Core, le nom du processus précédent a été *dnx.exe*.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Cliquez sur **Attacher**.

8. Ouvrez le site web de l’ordinateur distant. Dans un navigateur, accédez à **http://\<nom_ordinateur_distant >**.
    
    La page web ASP.NET doit s’afficher.
9. Dans l’application ASP.NET en cours d’exécution, cliquez sur le lien vers le **sur** page.

    Le point d’arrêt doit être atteint dans Visual Studio.

### <a name="bkmk_openports"></a> Résolution des problèmes : Ouvrir les ports requis sur Windows Server

Dans la plupart des configurations, les ports requis sont ouverts par l’installation d’ASP.NET et le débogueur distant. Toutefois, si vous dépannez les problèmes de déploiement et l’application est hébergée derrière un pare-feu, vous devez vérifier que les ports appropriés sont ouverts.

Sur une machine virtuelle Azure, vous devez ouvrir les ports via la [groupe de sécurité réseau](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Ports requis :

- 80 - requis pour IIS
- 4022 - requis pour le débogage distant à partir de Visual Studio 2017 (consultez [affectations de Port du débogueur distant](../debugger/remote-debugger-port-assignments.md) pour plus d’informations).
- UDP 3702 - port de détection de (facultatif) vous permet du **trouver** bouton lors de l’attachement du débogueur distant dans Visual Studio.

En outre, ces ports doivent déjà être ouverts par l’installation de ASP.NET :
- 8172 - (facultatif) requis pour Web Deploy déployer l’application à partir de Visual Studio

