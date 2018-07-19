---
title: Déployer ASP.NET sur IIS à l’aide de Web Deploy
ms.custom: ''
ms.date: 06/04/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
ms.assetid: 9cb339b5-3caf-4755-aad1-4a5da54b2a23
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 4705ca6e72001f8930e2fa4270515df53e1213a8
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080848"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>Déployer ASP.NET sur un ordinateur IIS distant à l’aide de Web Deploy dans Visual Studio

Cet article explique comment paramétrer et configurer une application Visual Studio 2017 ASP.NET MVC 4.5.2 et déployez-la sur IIS. Cet article contient des instructions sur la configuration d’une configuration de base d’IIS sur Windows server et le déploiement de l’application à partir de Visual Studio. Ces étapes sont inclus pour vous assurer que le serveur a exigé des composants installés et que vous êtes prêt à déployer. Si vous déployez une application ASP.NET Core, certaines étapes sont différentes. Pour déployer une application ASP.NET Core, consultez [publier une application à IIS en important les paramètres de publication](../deployment/tutorial-import-publish-settings-iis.md) pour obtenir des instructions. Dans certains scénarios ASP.NET et ASP.NET Core, il est plus rapide à déployer sur IIS en important les paramètres de publication.

Ces procédures ont été testées sur ces configurations de serveur :
* Windows Server 2012 R2 et IIS 8 (pour Windows Server 2008 R2, les étapes de serveur sont différents)

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Créer l’ASP.NET 4.5.2 application sur l’ordinateur Visual Studio
  
1. Sur l’ordinateur exécutant Visual Studio, choisissez **fichier** > **nouveau projet**.

1. Sous **Visual C#** ou **Visual Basic**, choisissez **Web**, puis dans le volet central **Application Web ASP.NET (.NET Framework)** puis cliquez sur **OK**.

    Si vous ne voyez pas les modèles de projet spécifiée, cliquez sur le **ouvrir Visual Studio Installer** lien dans le volet gauche de la **nouveau projet** boîte de dialogue. Visual Studio Installer est lancé. Consultez les conditions préalables dans cet article pour identifier les charges de travail Visual Studio requis, que vous devez installer.

1. Choisissez **MVC** (.NET Framework) et assurez-vous que l’option **aucune authentification** est sélectionnée, puis cliquez sur **OK**.

1. Tapez un nom tel que **MyWebApp** et cliquez sur **OK**.

    Visual Studio crée le projet.

1. Choisissez **Build** > **générer la Solution** pour générer le projet.

## <a name="install-and-configure-iis-on-windows-server"></a>Installer et configurer IIS sur Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Mettre à jour les paramètres de sécurité de navigateur sur Windows Server

Si la Configuration de sécurité renforcée est activée dans Internet Explorer (il est activé par défaut), vous devrez peut-être ajouter des domaines comme sites approuvés pour vous permettre de télécharger certaines des composants de serveur web. Ajouter les sites de confiance en accédant à **Options Internet** > **sécurité** > **Sites de confiance** > **Sites** . Ajoutez les domaines suivants.

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Lorsque vous téléchargez le logiciel, vous pouvez obtenir des demandes pour accorder des autorisations requises pour charger des différents scripts de site web et des ressources. Certaines de ces ressources ne sont pas nécessaires, mais pour simplifier le processus, cliquez sur **ajouter** lorsque vous y êtes invité.

## <a name="install-aspnet-45-on-windows-server"></a>Installer ASP.NET 4.5 sur Windows Server

Si vous souhaitez des informations plus détaillées pour installer ASP.NET sur IIS, consultez [IIS 8.0 à l’aide d’ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Dans le volet gauche du Gestionnaire de serveur, sélectionnez **IIS**. Cliquez sur le serveur et sélectionnez **Internet Information Services (IIS) Manager**.

1. Web Platform Installer (WebPI) permet d’installer ASP.NET 4.5 (à partir du nœud de serveur dans Windows Server 2012 R2, choisissez **obtenir nouveaux composants Web Platform** , puis recherchez ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Si vous utilisez Windows Server 2008 R2, installez ASP.NET 4 au lieu d’utiliser cette commande :

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Redémarrez le système (ou exécutez **net stop was /y** suivie **net démarrer w3svc** à partir d’une invite de commandes à assimiler à une modification apportée à la variable système PATH).

## <a name="install-web-deploy-36-on-windows-server"></a>Installation Web déployer 3.6 sur Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="configure-aspnet-web-site-on-the-windows-server-computer"></a>Configurer le site Web ASP.NET sur l’ordinateur Windows Server

1. Ouvrez l’Explorateur Windows et créez un dossier, **C:\Publish**, où vous allez déployer ultérieurement le projet ASP.NET.

2. Si elle n’est pas déjà ouverte, ouvrez le **Internet Information Services (IIS) Manager**. (Dans le volet gauche du Gestionnaire de serveur, sélectionnez **IIS**. Cliquez sur le serveur et sélectionnez **Internet Information Services (IIS) Manager**.)

3. Sous **connexions** dans le volet gauche, accédez à **Sites**.

4. Sélectionnez le **Site Web par défaut**, choisissez **paramètres de base**et définissez le **chemin d’accès physique** à **C:\Publish**.

5. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.

6. Définir le **Alias** champ **MyASPApp**, acceptez la valeur par défaut du Pool d’applications (**DefaultAppPool**) et définissez le **chemin d’accès physique** à  **C:\Publish**.

7. Sous **connexions**, sélectionnez **Pools d’applications**. Ouvrez **DefaultAppPool** et définissez le champ pool d’applications sur **ASP.NET v4.0** (ASP.NET 4.5 n’est pas une option pour le pool d’applications).

8. Avec le site sélectionné dans le Gestionnaire IIS, choisissez **modifier les autorisations**et assurez-vous que IUSR, IIS_IUSRS ou l’utilisateur configuré pour le Pool d’applications est un utilisateur autorisé avec des droits de lecture et exécution. Si aucun de ces utilisateurs sont présentes, ajoutez IUSR en tant qu’utilisateur disposant de droits de lecture et exécution.

## <a name="publish-and-deploy-the-app-using-web-deploy-from-visual-studio"></a>Publier et déployer l’application à l’aide de Web Deploy à partir de Visual Studio

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

En outre, vous devrez peut-être lire la section suivante sur la façon de résoudre les problèmes de ports.

## <a name="troubleshoot-open-required-ports-on-windows-server"></a>Résoudre les problèmes : Ouvrir les ports requis sur Windows Server

Dans la plupart des configurations, les ports requis sont ouverts par l’installation d’ASP.NET et Web Deploy. Toutefois, vous devrez peut-être vérifier que les ports sont ouverts.

> [!NOTE]
> Sur une machine virtuelle Azure, vous devez ouvrir les ports via la [groupe de sécurité réseau](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Ports requis :

* 80 - requises pour IIS
* 8172, requises pour Web Deploy pour déployer l’application à partir de Visual Studio

1. Pour ouvrir un port sur Windows Server, ouvrez le **Démarrer** menu, recherchez **pare-feu Windows avec fonctions avancées de sécurité**.

2. Puis choisissez **règles de trafic entrant** > **nouvelle règle** > **Port**. Choisissez **suivant** et sous **ports locaux spécifiques**, entrez le numéro de port, cliquez sur **suivant**, puis **autoriser la connexion**, cliquez sur Suivant, et Ajoutez le nom (**IIS**, **Web Deploy**, ou **msvsmon**) pour la règle de trafic entrant.

    Si vous souhaitez plus d’informations sur la configuration des pare-feu de Windows, consultez [configurer le pare-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Créer des règles supplémentaires pour les autres ports nécessaires.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous créé un fichier de paramètres de publication importé dans Visual Studio et déployé une application ASP.NET sur IIS. Vous pouvez également déployer en important les paramètres de publication.

> [!div class="nextstepaction"]
> [Déployer sur IIS en important les paramètres de publication](../deployment/tutorial-import-publish-settings-iis.md)
