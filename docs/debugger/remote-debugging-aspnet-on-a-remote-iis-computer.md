---
title: "ASP.NET Core sur un ordinateur distant IIS de débogage à distance | Documents Microsoft"
ms.custom: remotedebugging
ms.date: 08/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: hero-article
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 883a9ad8660204462d5aaa852ab87c5420af4382
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio-2017"></a>Débogage distant ASP.NET Core sur un ordinateur IIS distant dans Visual Studio 2017
Pour déboguer une application ASP.NET qui a été déployée sur IIS, installer et exécuter les outils à distance sur l’ordinateur où vous avez déployé votre application puis attachez à votre application en cours d’exécution à partir de Visual Studio.

![Composants du débogueur distant](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Ce guide explique comment installer et configurer un Visual Studio 2017 ASP.NET Core, déployez-le sur IIS et attacher le débogueur distant à partir de Visual Studio. Pour déboguer à distance ASP.NET 4.5.2, consultez [ASP.NET de déboguer à distance sur un ordinateur IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Vous pouvez également déployer et déboguer sur IIS à l’aide d’Azure. Pour plus d’informations, consultez [de débogage à distance sur Azure](../debugger/remote-debugging-azure.md).

Ces procédures ont été testées sur ces configurations de serveur :
* Windows Server 2012 R2 et IIS 10
* Windows Server 2016 et IIS 10

## <a name="requirements"></a>Spécifications

Débogage entre deux ordinateurs connectés via un proxy n’est pas pris en charge. Débogage sur une latence élevée ou d’une connexion à faible bande passante, telles que les connexions à distance d’Internet, ou via Internet entre des pays n’est pas recommandé et peut échouer ou être trop faibles. Pour obtenir une liste complète des conditions requises, consultez [exigences](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="create-the-aspnet-core-application-on-the-visual-studio-2017-computer"></a>Créer l’application ASP.NET Core sur l’ordinateur Visual Studio 2017 

1. Créez une application ASP.NET Core. (**Fichier > Nouveau > projet**, puis sélectionnez **Visual c# > Web > Application ASP.NET Core Web (.NET Core)** .

    Dans le **ASP.NET Core** section modèles, sélectionnez **Application Web**.

2. Assurez-vous que **activer la prise en charge Docker** est **pas** sélectionné et que **authentification** a la valeur **aucune authentification**.

3. Nommez le projet **MyASPApp** et cliquez sur **OK** pour créer la nouvelle solution.

4. Ouvrez le fichier About.cshtml.cs et définir un point d’arrêt dans le `OnGet` (méthode) (dans les modèles plus anciens, ouvrez plutôt HomeController.cs et définissez le point d’arrêt le `About()` méthode).

## <a name="bkmk_configureIIS"></a>Installer et configurer IIS sur Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Mettre à jour les paramètres de sécurité de navigateur sur Windows Server

En fonction de vos paramètres de sécurité, il peut gagner du temps d’ajouter les sites de confiance suivants à votre navigateur vous pouvez facilement télécharger le logiciel décrit dans ce didacticiel. Accès à ces sites peuvent être nécessaires :

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- VisualStudio.com

Si vous utilisez Internet Explorer, vous pouvez ajouter les sites de confiance en accédant à **Options Internet > sécurité > Sites de confiance > Sites**. Ces étapes sont différents pour d’autres navigateurs.

Lorsque vous téléchargez le logiciel, vous pouvez obtenir des demandes pour accorder des autorisations requises pour charger les différents scripts de site web et des ressources. Dans la plupart des cas, les ressources supplémentaires suivantes ne sont pas requis pour installer le logiciel.

## <a name="install-aspnet-core-on-windows-server"></a>Installez ASP.NET Core sur Windows Server

1. Installer le [hébergement sur serveur Windows .NET Core](https://go.microsoft.com/fwlink/?linkid=844461) offre groupée sur le système hôte. L’application installe le .NET Core Runtime, bibliothèque principale de .NET et le Module de base ASP.NET.

    > [!NOTE]
    > Si le système ne dispose d’une connexion Internet, obtenez et installez le  *[redistribuable Microsoft Visual C++ 2015](https://www.microsoft.com/download/details.aspx?id=53840)*  avant d’installer l’application d’hébergement sur serveur Windows .NET Core.

3. Redémarrer le système (ou exécutez **net stop a été /y** suivie **net démarrer w3svc** à partir d’une invite de commandes pour voir une modification dans le chemin d’accès du système).

## <a name="BKMK_install_webdeploy"></a>(Facultatif) Installation Web déployer 3.6 sur Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a>Configurer le site Web ASP.NET sur l’ordinateur Windows Server

1. Ouvrez l’Explorateur Windows et créez un dossier, **C:\Publish**, où vous déploierez plus tard le projet ASP.NET.

2. Ouvrez le **Internet Information Services (IIS) Manager**. (Dans le volet gauche du Gestionnaire de serveur, sélectionnez **IIS**. Cliquez sur le serveur et sélectionnez **Gestionnaire des Services Internet (IIS)**.)

3. Sous **connexions** dans le volet gauche, accédez à **Sites**.

4. Sélectionnez le **Site Web par défaut**, choisissez **les paramètres de base**et définissez la **chemin d’accès physique** à **C:\Publish**.

4. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.

5. Définir le **Alias** au champ **MyASPApp**, acceptez la valeur par défaut du Pool d’applications (**DefaultAppPool**) et définissez la **chemin d’accès physique** à  **C:\Publish**.

6. Sous **connexions**, sélectionnez **Pools d’applications**. Ouvrez **DefaultAppPool** et la valeur du champ de pool d’applications **aucun Code managé**.

7. Cliquez sur le nouveau site dans le Gestionnaire des services Internet, choisissez **modifier les autorisations**et assurez-vous que IUSR, IIS_IUSRS ou l’utilisateur configuré pour l’accès à l’application web est un utilisateur autorisé avec des droits de lecture et exécution.

    Si vous ne voyez pas un de ces utilisateurs avec accès, suivez les étapes pour ajouter IUSR en tant qu’utilisateur avec des droits de lecture et exécution.

## <a name="bkmk_webdeploy"></a>(Facultatif) Publier et déployer l’application à l’aide de Web Deploy à partir de Visual Studio

[!INCLUDE [remote-debugger-deploy-app-web-deploy](../debugger/includes/remote-debugger-deploy-app-web-deploy.md)]

## <a name="optional-publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>(Facultatif) Publier et déployer l’application en publiant dans un dossier local à partir de Visual Studio

Vous pouvez également publier et déployer l’application à l’aide du système de fichiers ou d’autres outils.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="BKMK_msvsmon"></a>Téléchargez et installez les outils à distance sur Windows Server

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

> [!TIP]
> Dans certains scénarios, il peut être plus efficace d’exécuter le débogueur distant à partir d’un partage de fichiers. Pour plus d’informations, consultez [exécuter le débogueur distant à partir d’un partage de fichiers](../debugger/remote-debugging.md#fileshare_msvsmon).
  
## <a name="BKMK_setup"></a>Configurer le débogueur distant sur Windows Server

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

## <a name="bkmk_openports"></a>Résolution des problèmes : Ouvrir les ports requis sur Windows Server

Dans la plupart des configurations, les ports requis sont ouverts par l’installation d’ASP.NET et le débogueur distant. Toutefois, vous devrez peut-être vérifier que les ports sont ouverts.

> [!NOTE]
> Sur une machine virtuelle Azure, vous devez ouvrir les ports via la [groupe de sécurité réseau](https://docs.microsoft.com/en-us/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Ports requis :

- 80 - requis pour IIS
- 4022 - requis pour le débogage distant à partir de Visual Studio 2017 (consultez [affectations de Port du débogueur distant](../debugger/remote-debugger-port-assignments.md) pour plus d’informations.
- 8172 - (facultatif) requis pour Web Deploy déployer l’application à partir de Visual Studio.
- UDP 3702 - port de détection de (facultatif) vous permet du **trouver** bouton lors de l’attachement du débogueur distant dans Visual Studio.

1. Pour ouvrir un port sur Windows Server, ouvrez le **Démarrer** menu, recherchez **pare-feu Windows avec fonctions avancées de sécurité**.

2. Puis choisissez **règles de trafic entrant > nouvelle règle > Port**, puis cliquez sur **suivant**. (Pour UDP 3702, choisissez **règles de trafic sortant** à la place.)

3. Sous **ports locaux spécifiques**, entrez le numéro de port, cliquez sur **suivant**.

4. Cliquez sur **autoriser la connexion**, cliquez sur **suivant**.

5. Sélectionnez un ou plusieurs types de réseau à activer pour le port, puis cliquez sur **suivant**.

    Les types que vous sélectionnez doivent inclure le réseau auquel l’ordinateur distant est connecté.
6. Ajoutez le nom (par exemple, **IIS**, **Web Deploy**, ou **msvsmon**) pour la règle de trafic entrant et cliquez sur **Terminer**.

    Vous devez voir votre nouvelle règle dans la liste des règles de trafic entrant et les règles de trafic sortant.

    Si vous souhaitez plus d’informations sur la configuration du pare-feu Windows, consultez [configurer le pare-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Créer des règles supplémentaires pour les autres ports requis.
