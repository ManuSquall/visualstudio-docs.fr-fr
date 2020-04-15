---
title: Debug à distance ASP.NET cœur sur un ordinateur à distance IIS (fr) Microsoft Docs
ms.custom: remotedebugging
ms.date: 05/21/2018
ms.topic: conceptual
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: b33ead969456935dab54c042ba4fbaf1f5ff44f4
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385476"
---
# <a name="remote-debug-aspnet-core-on-a-remote-iis-computer-in-visual-studio"></a>Remote Debug ASP.NET Core sur un ordinateur à distance IIS dans Visual Studio

Pour déboguer une application ASP.NET Core qui a été déployée dans l’IIS, installez et exécutez les outils distants de l’ordinateur où vous avez déployé votre application, puis attachez-vous à votre application en cours d’exécution à partir de Visual Studio.

![Composants de débbuggeurs à distance](../debugger/media/remote-debugger-aspnet.png "Remote_debugger_components")

Ce guide explique comment configurer et configurer un studio visuel ASP.NET Core, le déployer à IIS et attacher le débbuggeur à distance de Visual Studio. Pour déboiffer à distance ASP.NET 4.5.2, voir [Remote Debug ASP.NET sur un ordinateur IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Vous pouvez également déployer et déboiffer sur IIS à l’aide d’Azure. Pour Azure App Service, vous pouvez facilement déployer et déboquer sur une instance préconfigurée de l’IIS et le débbuggeur à distance en utilisant soit le [Snapshot Debugger](../debugger/debug-live-azure-applications.md) ou [en attachant le débbugger de Server Explorer](../debugger/remote-debugging-azure.md).

## <a name="prerequisites"></a>Prérequis

::: moniker range=">=vs-2019"
Visual Studio 2019 est tenu de suivre les étapes indiquées dans cet article.
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017 est tenu de suivre les étapes indiquées dans cet article.
::: moniker-end

Ces procédures ont été testées sur ces configurations de serveur :
* Windows Server 2012 R2 et IIS 8
* Windows Server 2016 et IIS 10

## <a name="network-requirements"></a>Configuration requise pour le réseau

Le débogage entre deux ordinateurs connectés par un proxy n’est pas pris en charge. Il n’est pas recommandé de déracyer une latence élevée ou une connexion à faible bande passante, comme Internet commutée ou sur Internet à travers les pays, et peut échouer ou être inacceptablement lent. Pour une liste complète des exigences, voir [Exigences](../debugger/remote-debugging.md#requirements_msvsmon).

## <a name="app-already-running-in-iis"></a>App déjà en cours d’exécution dans IIS?

Cet article comprend des étapes sur la configuration d’une configuration de base de l’IIS sur le serveur Windows et le déploiement de l’application à partir de Visual Studio. Ces étapes sont incluses pour s’assurer que le serveur a besoin de composants installés, que l’application peut fonctionner correctement, et que vous êtes prêt à déboguer à distance.

* Si votre application est en cours d’exécution dans IIS et que vous voulez juste télécharger le débbugger à distance et commencer à débogage, aller à [Télécharger et installer les outils à distance sur Windows Server](#BKMK_msvsmon).

* Si vous voulez de l’aide pour vous assurer que votre application est configurée, déployée et correctement en cours d’exécution dans l’IIS afin que vous puissiez déboguer, suivez toutes les étapes de ce sujet.

## <a name="create-the-aspnet-core-application-on-the-visual-studio-computer"></a>Créez l’application ASP.NET Core sur l’ordinateur Visual Studio

1. Créez une application web ASP.NET Core. 

    ::: moniker range=">=vs-2019"
    Dans Visual Studio 2019, tapez **Ctrl Q** pour ouvrir la boîte de recherche, **tapez asp.net**, choisissez **Templates**, puis choisissez **Créer de nouvelles ASP.NET’application Web de base.** Dans la boîte de dialogue qui apparaît, nom du projet **MyASPApp**, puis choisissez **Create**. Ensuite, choisissez **l’application Web (Model-View-Controller)**, puis choisissez **Créer**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dans Visual Studio 2017, choisissez **File > New > Project**, puis sélectionnez Visual C > Web > ASP.NET Core Web **Application**. Dans la section ASP.NET modèles de base, sélectionnez **l’application Web (Model-View-Controller)**. Assurez-vous que ASP.NET Core 2.1 est sélectionné, que **le support Enable Docker** n’est pas sélectionné et que **l’authentification** est définie **à Aucune authentification**. Nommez le projet **MyASPApp**.
    ::: moniker-end

4. Ouvrez le fichier About.cshtml.cs et définissez `OnGet` un point d’arrêt dans la méthode (dans les `About()` anciens modèles, ouvrez HomeController.cs à la place et définissez le point d’arrêt dans la méthode).

## <a name="install-and-configure-iis-on-windows-server"></a><a name="bkmk_configureIIS"></a>Installer et configurer IIS sur Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Mettre à jour les paramètres de sécurité du navigateur sur Windows Server

Si la configuration de sécurité améliorée est activée dans Internet Explorer (elle est activée par défaut), alors vous devrez peut-être ajouter certains domaines comme sites de confiance pour vous permettre de télécharger certains des composants du serveur Web. Ajoutez les sites de confiance en vous rendant à **Internet Options > Sécurité > sites de confiance > sites**. Ajoutez les domaines suivants.

- microsoft.com
- go.microsoft.com
- download.microsoft.com
- iis.net

Lorsque vous téléchargez le logiciel, vous pouvez obtenir des demandes d’autorisation d’accorder la permission de charger divers scripts et ressources de site Web. Certaines de ces ressources ne sont pas nécessaires, mais pour simplifier le processus, cliquez sur **Ajouter** lorsqu’on l’incite.

## <a name="install-aspnet-core-on-windows-server"></a>Installer ASP.NET Core sur Windows Server

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

1. Ouvrez Windows Explorer et créez un nouveau dossier, **C: 'Publish**, où vous déployez plus tard le projet ASP.NET Core.

2. S’il n’est pas déjà ouvert, ouvrez le **gestionnaire des services d’information sur Internet (IIS).** (Dans le volet gauche de Server Manager, sélectionnez **IIS**. Cliquez à droite sur le serveur et sélectionnez **le gestionnaire des services d’information Internet (IIS).**

3. Sous **connexions** dans la vitre gauche, allez à **Sites**.

4. Sélectionnez le **site Web par défaut**, choisissez les paramètres de **base**et définissez le **chemin physique** vers **C: 'Publier**.

4. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.

5. Définissez le champ **Alias** sur **MyASPApp**, acceptez le pool d’applications par défaut (**DefaultAppPool**), et définissez le **chemin physique** vers **C: 'Publish**.

6. Sous **connexions**, sélectionnez **Les pools d’applications**. Ouvrez **DefaultAppPool** et définissez le champ de piscine d’application en **aucun code géré**.

7. Cliquez à droite sur le nouveau site dans le gestionnaire IIS, choisissez **Edit Permissions**, et assurez-vous que IUSR, IIS_IUSRS ou l’utilisateur configuré pour accéder à l’application web est un utilisateur autorisé avec lire & les droits d’exécution.

    Si vous ne voyez pas l’un de ces utilisateurs avec accès, passez par des étapes pour ajouter IUSR en tant qu’utilisateur avec Lire & Les droits d’exécution.

### <a name="publish-and-deploy-the-app-by-publishing-to-a-local-folder-from-visual-studio"></a>Publier et déployer l’application en publiant dans un dossier local de Visual Studio

Vous pouvez également publier et déployer l’application à l’aide du système de fichiers ou d’autres outils.

[!INCLUDE [remote-debugger-deploy-app-local](../debugger/includes/remote-debugger-deploy-app-local.md)]

## <a name="download-and-install-the-remote-tools-on-windows-server"></a><a name="BKMK_msvsmon"></a>Téléchargez et installez les outils distants sur Windows Server

Téléchargez la version des outils distants qui correspondent à votre version de Visual Studio.

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

## <a name="set-up-the-remote-debugger-on-windows-server"></a><a name="BKMK_setup"></a>Configurez le débbugger à distance sur Windows Server

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

> [!NOTE]
> Si vous avez besoin d’ajouter des autorisations pour d’autres utilisateurs, modifier le mode d’authentification, ou le numéro de port pour le débbugger à distance, voir [Configure Configurer le débbugger à distance](../debugger/remote-debugging.md#configure_msvsmon).

Pour plus d’informations sur l’exécution du débbugger à distance comme un service, voir [Exécuter le débbugger à distance comme un service](../debugger/remote-debugging.md#bkmk_configureService).

## <a name="attach-to-the-aspnet-application-from-the-visual-studio-computer"></a><a name="BKMK_attach"></a>Joindre à l’application ASP.NET à partir de l’ordinateur Visual Studio

1. Sur l’ordinateur Visual Studio, ouvrez la solution que vous essayez de déboiffer (**MyASPApp** si vous suivez toutes les étapes de cet article).
2. Dans Visual Studio, cliquez sur **Debug > Attach to Process** (Ctrl et Alt et P).

    > [!TIP]
    > Dans Visual Studio 2017 et les versions ultérieures, vous pouvez rattacher au même processus que vous avez précédemment attaché en utilisant **Debug > Reattach to Process...** (Shift ' Alt 'P).

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

    * Si vous utilisez le [modèle d’hébergement intégré](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1#hosting-models) sur IIS, sélectionnez le processus **w3wp.exe** correct. À partir de .NET Core 3, c’est la valeur par défaut.

    * Sinon, sélectionnez le processus **dotnet.exe.** (C’est le modèle d’hébergement hors-processus.)

    Si vous avez plusieurs processus montrant *w3wp.exe* ou *dotnet.exe*, consultez la colonne **nom de l’utilisateur.** Dans certains scénarios, la colonne **Nom de l’utilisateur** affiche le nom de votre pool d’applications, comme **IIS APPPOOL-DefaultAppPool**. Si vous voyez le Pool App, mais ce n’est pas unique, créez un nouveau pool d’applications nommé pour l’instance d’application que vous souhaitez déboiffer, puis vous pouvez le trouver facilement dans la colonne **nom de l’utilisateur.**

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

## <a name="troubleshooting-open-required-ports-on-windows-server"></a><a name="bkmk_openports"></a> Résolution des problèmes Ouvrez les ports requis sur Windows Server

Dans la plupart des configurations, les ports requis sont ouverts par l’installation de ASP.NET et le débbugger à distance. Toutefois, vous devrez peut-être vérifier que les ports sont ouverts.

> [!NOTE]
> Sur un Azure VM, vous devez ouvrir des ports via le [groupe de sécurité Réseau](/azure/virtual-machines/windows/nsg-quickstart-portal).

Ports requis :

* 80 - Nécessaire pour l’IIS
::: moniker range=">=vs-2019"
* 4024 - Nécessité pour le débogage à distance de Visual Studio 2019 (voir [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) pour plus d’informations).
::: moniker-end
::: moniker range="vs-2017"
* 4022 - Nécessité d’un débogage à distance à partir de Visual Studio 2017 (voir [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md) pour plus d’informations).
::: moniker-end
* UDP 3702 - (Facultatif) Le port Discovery vous permet de passer le bouton **Trouver** lors de l’attachement au débbuggeur à distance de Visual Studio.

1. Pour ouvrir un port sur Windows Server, ouvrez le menu **Démarrer,** recherchez **le pare-feu Windows avec Advanced Security**.

2. Ensuite, choisissez **les règles entrantes > nouvelle règle > Port**, puis cliquez sur **Next**. (Pour UDP 3702, choisissez plutôt **les règles sortantes.)**

3. Sous **des ports locaux spécifiques**, entrez le numéro de port, cliquez sur **Next**.

4. Cliquez **sur Autoriser la connexion**, cliquez sur **Suivant**.

5. Sélectionnez un ou plusieurs types de réseau pour activer le port et cliquez sur **Next**.

    Les types que vous sélectionnez doivent inclure le réseau auquel l’ordinateur distant est connecté.
6. Ajoutez le nom (par exemple, **IIS**, **Web Deploy**, ou **msvsmon**) pour la règle entrante et cliquez sur **Finition**.

    Vous devez voir votre nouvelle règle dans la liste Règles de trafic entrant ou Règles de trafic sortant.

    Si vous voulez plus de détails sur la configuration du pare-feu Windows, voir [Configurer le pare-feu Windows pour Remote Debugging](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Créer des règles supplémentaires pour les autres ports requis.
