---
title: "À distance déboguer des noyaux de ASP.NET sur IIS et Azure | Documents Microsoft"
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6c04b53-d1b9-4552-a8fd-3ed6f4902ce6
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0527d33e47ce42449f2ae2bb75ee3e342b04c2b
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2017
---
# <a name="remote-debug-aspnet-core-on-iis-and-azure-in-visual-studio-2017"></a>Débogage distant ASP.NET Core IIS et sur Azure dans Visual Studio 2017
Vous pouvez déployer une application Web ASP.NET sur un ordinateur Windows Server avec les services IIS et de le configurer pour le débogage distant. Ce guide explique comment installer et configurer une application Visual Studio 2017 ASP.NET Core, déployez-le sur IIS à l’aide d’Azure et attacher le débogueur distant à partir de Visual Studio.

> [!WARNING]
> Veillez à supprimer les ressources Azure que vous créez lorsque vous avez effectué les étapes de ce didacticiel. De cette façon, que vous pouvez éviter d’encourir de frais inutiles.

Cette rubrique montre comment :

* Débogage distant ASP.NET Core sur un Service d’application Azure

* Débogage distant ASP.NET Core sur une machine virtuelle Azure

Pour le Service d’applications Azure, vous devez déployer votre application à partir de Visual Studio vers Azure, mais vous n’avez pas besoin d’installez manuellement ou configurer les services IIS ou le débogueur distant (ces composants sont représentées par des lignes pointillées), comme indiqué dans l’illustration suivante.

![Composants du débogueur distant](../debugger/media/remote-debugger-azure-app-service.png "Remote_debugger_components")

Pour une machine virtuelle Azure, vous devez déployer votre application à partir de Visual Studio vers Azure, et vous devez également installer manuellement le rôle IIS et le débogueur distant, comme indiqué dans l’illustration suivante.

![Composants du débogueur distant](../debugger/media/remote-debugger-azure-vm.png "Remote_debugger_components")

> [!NOTE]
> Pour déboguer des noyaux de ASP.NET sur Azure Service Fabric, consultez [déboguer une application de Service Fabric distante](/azure/service-fabric/service-fabric-debugging-your-application#debug-a-remote-service-fabric-application).

### <a name="requirements"></a>Spécifications

Débogage entre deux ordinateurs connectés via un proxy n’est pas pris en charge. Débogage sur une latence élevée ou d’une connexion à faible bande passante, telles que les connexions à distance d’Internet, ou via Internet entre des pays n’est pas recommandé et peut échouer ou être trop faibles. Pour obtenir une liste complète des conditions requises, consultez [exigences](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Créer l’application ASP.NET Core sur l’ordinateur Visual Studio 2017 

1. Créez une application ASP.NET Core. (Choisissez **fichier > Nouveau > projet**, puis sélectionnez **Visual c# > Web > Application ASP.NET Core Web (.NET Core)**).

    Dans le **ASP.NET Core** section modèles, sélectionnez **Application Web**.

2. Assurez-vous que **activer la prise en charge Docker** est **pas** sélectionné et que **authentification** a la valeur **aucune authentification**.

3. Nommez le projet **MyASPApp** et cliquez sur **OK** pour créer la nouvelle solution.

4. Ouvrez le fichier About.cshtml.cs et définir un point d’arrêt dans le `OnGet` (méthode) (dans les modèles plus anciens, ouvrez plutôt HomeController.cs et définissez le point d’arrêt le `About()` méthode).

## <a name="remote-debug-aspnet-core-on-an-azure-app-service"></a>Débogage distant ASP.NET Core sur un Service d’application Azure

À partir de Visual Studio, vous pouvez rapidement publier et déboguer votre application à une instance entièrement d’IIS. Toutefois, la configuration d’IIS est prédéfinie et vous ne pouvez pas personnaliser. Pour obtenir des instructions détaillées, consultez [déployer une application de web ASP.NET Core pour Azure à l’aide de Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). (Si vous avez besoin de la possibilité de personnaliser IIS, essayer de déboguer un [Azure VM](#BKMK_azure_vm).) 

#### <a name="to-deploy-the-app-and-remote-debug"></a>Pour déployer l’application et le débogage distant

1. Dans Visual Studio, cliquez sur le nœud du projet et choisissez **publier**.

2. Choisissez **Microsoft Azure App Service** à partir de la **publier** boîte de dialogue, sélectionnez **créer un nouveau**et suivez les invites à publier.

    Pour obtenir des instructions détaillées, consultez [déployer une application de web ASP.NET Core pour Azure à l’aide de Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

3. Dans **l’Explorateur de serveurs**, avec le bouton droit sur l’instance de Service de l’application et choisissez **attacher le débogueur**.

4. Dans l’application ASP.NET en cours d’exécution, cliquez sur le lien vers le **sur** page.

    Le point d’arrêt doit être atteint dans Visual Studio.

    Voilà ! Le reste des étapes de cette rubrique s’appliquent au débogage distant sur une machine virtuelle Azure.

## <a name="BKMK_azure_vm"></a>Débogage distant ASP.NET Core sur une machine virtuelle Azure

Vous pouvez créer une machine virtuelle Azure pour Windows Server et puis installer et configurer IIS et les autres composants logiciels requis. Cela prend plus de temps que le déploiement à un Service d’application Azure et requiert que vous suivez les étapes restantes dans ce didacticiel.

Tout d’abord, suivez toutes les étapes décrites dans [installer et exécuter IIS](/azure/virtual-machines/virtual-machines-windows-hero-role).

Lorsque vous ouvrez le port 80 dans le groupe de sécurité réseau, vous devez également ouvrir le port 4022 pour le débogueur distant. De cette façon, vous ne devez ouvrir ultérieurement.

### <a name="update-browser-security-settings-on-windows-server"></a>Mettre à jour les paramètres de sécurité de navigateur sur Windows Server

En fonction des paramètres de sécurité de votre navigateur, il peut gagner du temps d’ajouter les sites de confiance suivants à votre navigateur vous pouvez facilement télécharger le logiciel décrit dans ce didacticiel. Accès à ces sites peuvent être nécessaires :

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- VisualStudio.com

Si vous utilisez Internet Explorer, vous pouvez ajouter les sites de confiance en accédant à **Options Internet > sécurité > Sites de confiance > Sites**. Ces étapes sont différents pour d’autres navigateurs. (Si vous avez besoin télécharger une version antérieure du débogueur distant à partir de my.visualstudio.com, certains sites de confiance supplémentaires sont requis pour se connecter).

Lorsque vous téléchargez le logiciel, vous pouvez obtenir des demandes pour accorder des autorisations requises pour charger les différents scripts de site web et des ressources. Dans la plupart des cas, les ressources supplémentaires suivantes ne sont pas requis pour installer le logiciel.

### <a name="install-aspnet-core-on-windows-server"></a>Installez ASP.NET Core sur Windows Server

1. Installer le [hébergement sur serveur Windows .NET Core](https://aka.ms/dotnetcore-2-windowshosting) offre groupée sur le système hôte. Le groupe va installer le .NET Core Runtime, bibliothèque principale de .NET et le Module de base ASP.NET. Pour obtenir des instructions plus détaillées, consultez [publication sur IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

    > [!NOTE]
    > Si le système ne dispose d’une connexion Internet, obtenez et installez le  *[redistribuable Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=53840)*  avant d’installer l’application d’hébergement sur serveur Windows .NET Core.

3. Redémarrer le système (ou exécutez **net stop a été /y** suivie **net démarrer w3svc** à partir d’une invite de commandes pour voir une modification dans le chemin d’accès du système).

### <a name="BKMK_install_webdeploy"></a>(Facultatif) Installation Web déployer 3.6 sur Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

### <a name="BKMK_deploy_asp_net"></a>Configurer le site Web ASP.NET sur l’ordinateur Windows Server

1. Ouvrez le **Gestionnaire des services Internet (IIS)** .et accédez à **Sites**.

2. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.

3. Définir le **Alias** au champ **MyASPApp** et le champ pool d’applications pour **aucun Code managé**. Définir le **chemin d’accès physique** à **C:\Publish** (où vous déploierez plus tard le projet ASP.NET).

4. Le site sélectionné dans le Gestionnaire des services Internet, choisissez **modifier les autorisations**et assurez-vous que IUSR, IIS_IUSRS ou l’utilisateur configuré pour le Pool d’applications est un utilisateur autorisé avec des droits de lecture et exécution.

    Si vous ne voyez pas un de ces utilisateurs avec accès, suivez les étapes pour ajouter IUSR en tant qu’utilisateur avec des droits de lecture et exécution.

### <a name="bkmk_webdeploy"></a>(Facultatif) Publier et déployer l’application à l’aide de Web Deploy à partir de Visual Studio

Si vous avez installé le déploiement Web à l’aide de Web Platform Installer, vous pouvez déployer l’application directement à partir de Visual Studio.

1. Démarrez Visual Studio avec des privilèges élevés et ouvrez à nouveau le projet.

    Cela peut être nécessaire pour déployer votre application à l’aide de Web Deploy.

2. Dans l’ **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet et sélectionnez **Publier**.

3. Pour **sélectionner une cible de publication**, sélectionnez **Machine virtuelle Microsoft Azure** et cliquez sur **publier**.

    ![RemoteDBG_Publish_IISl](../debugger/media/remotedbg_azure_vm_profile.png "RemoteDBG_Publish_IIS")

4. Dans la boîte de dialogue, sélectionnez l’ordinateur virtuel Azure que vous avez créé précédemment.

4. Entrez les paramètres de configuration de correction pour la configuration de votre machine virtuelle Azure et IIS.

    ![RemoteDBG_Publish_WebDeployl](../debugger/media/remotedbg_iis_webdeploy_config.png "RemoteDBG_Publish_WebDeploy")

    Si un nom d’hôte ne résout pas lorsque vous essayez de validation en suivant les étapes le **Server** texte zone, essayez de l’adresse IP. Assurez-vous que vous utilisez le port 80 dans le **Server** texte zone et vous assurer que le port 80 est ouvert dans le pare-feu.

6. Cliquez sur **suivant**, choisissez un **déboguer** configuration, choisissez **supprimer les fichiers supplémentaires à la destination** sous le **fichier publier** Options.

5. Cliquez sur **Prev**, puis choisissez **Validate**. Si le programme d’installation de connexion valide, essayez de publier.

6. Cliquez sur **publier** pour publier l’application.

    L’onglet sortie vous indiquera si la publication a réussi, et l’application s’ouvre dans votre navigateur.

    Si vous obtenez une erreur mentionnant Web Deploy, vérifiez à nouveau les étapes d’installation Web Deploy et assurez-vous que le [correct ports sont ouverts](#bkmk_openports) se trouvent sur le serveur.

    Si l’application se déploie correctement, mais elle ne s’exécute pas correctement, vérifiez que IIS et votre projet Visual Studio utilisent la même version de ASP.NET. Si c'est-à-dire pas le problème, il peut être un problème avec votre configuration d’IIS ou de la configuration de votre site Web. Sur le serveur Windows, ouvrez le site Web d’IIS pour les messages d’erreur plus spécifiques et puis revérifiez les étapes précédentes.

### <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Facultatif) Publier et déployer l’application en publiant dans un dossier local à partir de Visual Studio

Si vous n’utilisez pas Web Deploy, vous devez publier et déployer l’application à l’aide du système de fichiers ou d’autres outils. Vous pouvez commencer par créer un package en utilisant le système de fichiers, puis déployer le package manuellement ou utiliser d’autres outils comme XCopy, RoboCopy ou PowerShell. Dans cette section, nous supposons que vous effectuez la copie manuellement le package si vous n’utilisez pas Web Deploy.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

### <a name="BKMK_msvsmon"></a>Téléchargez et installez les outils à distance sur Windows Server

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]
  
### <a name="BKMK_setup"></a>Configurer le débogueur distant sur Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si vous devez ajouter des autorisations pour les utilisateurs supplémentaires, modifier le mode d’authentification ou numéro de port pour le débogueur distant, consultez [configurer le débogueur distant](../debugger/remote-debugging.md#configure_msvsmon).

### <a name="BKMK_attach"></a> Attachement à l’application ASP.NET à partir de l’ordinateur Visual Studio

1. Sur l’ordinateur Visual Studio, ouvrez le **MyASPApp** solution.
2. Dans Visual Studio, cliquez sur **Déboguer > Attacher au processus** (Ctrl + Alt + P).

    > [!TIP]
    > Dans Visual Studio 2017, vous pouvez attacher au nouveau pour le même processus que vous précédemment attaché à l’aide de **Déboguer > rattacher à un processus en cours...** (Maj + Alt + P). 

3. Définissez le champ qualificateur sur  **\<nom_ordinateur_distant > : 4022**.
4. Cliquez sur **Actualiser**.
    Des processus doivent s’afficher dans la fenêtre **Processus disponibles** .

    Si vous ne voyez pas tous les processus, essayez d’utiliser l’adresse IP au lieu du nom de l’ordinateur distant (le port est requis). Vous pouvez utiliser `ipconfig` dans une ligne de commande pour obtenir l’adresse IPv4.

    Si vous souhaitez utiliser le **trouver** bouton, vous devrez peut-être [ouvrir le port UDP 3702](#bkmk_openports) sur le serveur.

5. Cochez  **Afficher les processus de tous les utilisateurs**.
6. Tapez la première lettre d’un nom de processus pour rechercher rapidement **dotnet.exe** (pour ASP.NET Core).
    >Remarque : Pour une application ASP.NET Core, le nom du processus précédent était dnx.exe.

    ![RemoteDBG_AttachToProcess](../debugger/media/remotedbg_attachtoprocess_aspnetcore.png "RemoteDBG_AttachToProcess")

7. Cliquez sur **Attacher**.

8. Ouvrez le site web de l’ordinateur distant. Dans un navigateur, accédez à **http://\<nom_ordinateur_distant >**.
    
    La page web ASP.NET doit s’afficher.
9. Dans l’application ASP.NET en cours d’exécution, cliquez sur le lien vers le **sur** page.

    Le point d’arrêt doit être atteint dans Visual Studio.

### <a name="bkmk_openports"></a>Résolution des problèmes : Ouvrir les ports requis sur Windows Server

Dans la plupart des configurations, les ports requis sont ouverts par l’installation d’ASP.NET et le débogueur distant. Toutefois, si vous dépannez les problèmes de déploiement et l’application est hébergée derrière un pare-feu, vous devez vérifier que les ports appropriés sont ouverts.

Sur une machine virtuelle Azure, vous devez ouvrir les ports via la [groupe de sécurité réseau](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Ports requis :

- 80 - requis pour IIS
- 4022 - requis pour le débogage distant à partir de Visual Studio 2017 (consultez [affectations de Port du débogueur distant](../debugger/remote-debugger-port-assignments.md) pour plus d’informations).
- UDP 3702 - port de détection de (facultatif) vous permet du **trouver** bouton lors de l’attachement du débogueur distant dans Visual Studio.

En outre, ces ports doivent déjà être ouverts par l’installation de ASP.NET :
- 8172 - (facultatif) requis pour Web Deploy déployer l’application à partir de Visual Studio

