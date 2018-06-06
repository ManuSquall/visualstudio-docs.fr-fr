---
title: Déployer de ASP.NET sur IIS à l’aide de Web Deploy
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
ms.openlocfilehash: a63d9947f544ddff1de81aaf34ed62c9646fba3d
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34794191"
---
# <a name="deploy-aspnet-to-a-remote-iis-computer-using-web-deploy-in-visual-studio"></a>Déployer de ASP.NET sur un ordinateur IIS distant à l’aide de Web Deploy dans Visual Studio

Cet article explique comment installer et configurer une application Visual Studio 2017 ASP.NET MVC 4.5.2 et déployez-le sur IIS. Cet article inclut les étapes de configuration de la configuration de base d’IIS sur Windows server et le déploiement de l’application à partir de Visual Studio. Ces étapes sont inclus pour vous assurer que le serveur a des composants installés et que vous êtes prêt à déployer. Si vous déployez une application ASP.NET Core, quelques étapes sont différents. Pour déployer une application ASP.NET Core, consultez [publier une application à IIS en important les paramètres de publication](../deployment/tutorial-import-publish-settings-iis.md) pour obtenir des instructions. Dans certains scénarios ASP.NET et ASP.NET Core, il est plus rapide pour déployer sur IIS en important les paramètres de publication.

Ces procédures ont été testées sur ces configurations de serveur :
* Windows Server 2012 R2 et IIS 8 (pour Windows Server 2008 R2, les étapes de serveur sont différentes)

## <a name="create-the-aspnet-452-application-on-the-visual-studio-computer"></a>Créer ASP.NET 4.5.2 application sur l’ordinateur Visual Studio
  
1. Sur l’ordinateur exécutant Visual Studio, choisissez **fichier > Nouveau projet**.

1. Sous **Visual C#** ou **Visual Basic**, choisissez **Web**, puis dans le volet central, choisissez soit **ASP.NET Web Applications (.NET Framework)** puis cliquez sur **OK**.

    Si vous ne voyez pas les modèles de projet spécifié, cliquez sur le **ouvrir Visual Studio Installer** lien dans le volet gauche de la **nouveau projet** boîte de dialogue. Visual Studio Installer est lancé. Consultez les conditions préalables dans cet article pour identifier les charges de travail Visual Studio requis, que vous devez installer.

1. Choisissez **MVC** (.NET Framework) et assurez-vous que **aucune authentification** est sélectionné, puis cliquez sur **OK**.

1. Tapez un nom tel que **MyWebApp** et cliquez sur **OK**.

    Visual Studio crée le projet.

1. Choisissez **Générer > Générer la Solution** pour générer le projet.

## <a name="bkmk_configureIIS"></a> Installer et configurer IIS sur Windows Server

[!INCLUDE [remote-debugger-install-iis-role](../debugger/includes/remote-debugger-install-iis-role.md)]

## <a name="update-browser-security-settings-on-windows-server"></a>Mettre à jour les paramètres de sécurité de navigateur sur Windows Server

Si la Configuration de sécurité renforcée est activée dans Internet Explorer (elle est activée par défaut), vous devez ajouter des domaines en tant que sites de confiance pour vous permettre de télécharger des composants de serveur web. Ajouter les sites de confiance en accédant à **Options Internet > sécurité > Sites de confiance > Sites**. Ajoutez les domaines suivants.

- Microsoft.com
- go.microsoft.com
- download.microsoft.com
- IIS.NET

Lorsque vous téléchargez le logiciel, vous pouvez obtenir des demandes pour accorder des autorisations requises pour charger les différents scripts de site web et des ressources. Certaines de ces ressources ne sont pas obligatoires, mais pour simplifier le processus, cliquez sur **ajouter** lorsque vous y êtes invité.

## <a name="BKMK_deploy_asp_net"></a> Installez ASP.NET 4.5 sur Windows Server

Si vous souhaitez des informations plus détaillées pour installer ASP.NET sur IIS, consultez [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

1. Dans le volet gauche du Gestionnaire de serveur, sélectionnez **IIS**. Cliquez sur le serveur et sélectionnez **Gestionnaire des Services Internet (IIS)**.

1. Web Platform Installer (WebPI) permet d’installer ASP.NET 4.5 (à partir du nœud de serveur dans Windows Server 2012 R2, choisissez **obtenir nouveaux composants Web Platform** , puis recherchez ASP.NET)

    ![RemoteDBG_IIS_AspNet_45](../debugger/media/remotedbg_iis_aspnet_45.png "RemoteDBG_IIS_AspNet_45")

    > [!NOTE]
    > Si vous utilisez Windows Server 2008 R2, installez ASP.NET 4 au lieu d’utiliser cette commande :

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Redémarrer le système (ou exécutez **net stop a été /y** suivie **net démarrer w3svc** à partir d’une invite de commandes pour voir une modification dans le chemin d’accès du système).

## <a name="BKMK_install_webdeploy"></a> Installation Web déployer 3.6 sur Windows Server

[!INCLUDE [remote-debugger-install-web-deploy](../debugger/includes/remote-debugger-install-web-deploy.md)]

## <a name="BKMK_deploy_asp_net"></a> Configurer le site Web ASP.NET sur l’ordinateur Windows Server

1. Ouvrez l’Explorateur Windows et créez un dossier, **C:\Publish**, où vous déploierez plus tard le projet ASP.NET.

2. Si elle n’est pas déjà ouverte, ouvrez le **Gestionnaire des Services Internet (IIS)**. (Dans le volet gauche du Gestionnaire de serveur, sélectionnez **IIS**. Cliquez sur le serveur et sélectionnez **Gestionnaire des Services Internet (IIS)**.)

3. Sous **connexions** dans le volet gauche, accédez à **Sites**.

4. Sélectionnez le **Site Web par défaut**, choisissez **les paramètres de base**et définissez la **chemin d’accès physique** à **C:\Publish**.

5. Cliquez avec le bouton droit sur le nœud **Site web par défaut** et sélectionnez **Ajouter une application**.

6. Définir le **Alias** au champ **MyASPApp**, acceptez la valeur par défaut du Pool d’applications (**DefaultAppPool**) et définissez la **chemin d’accès physique** à  **C:\Publish**.

7. Sous **connexions**, sélectionnez **Pools d’applications**. Ouvrez **DefaultAppPool** et la valeur du champ de pool d’applications **ASP.NET v4.0** (ASP.NET 4.5 n’est pas une option pour le pool d’applications).

8. Le site sélectionné dans le Gestionnaire des services Internet, choisissez **modifier les autorisations**et assurez-vous que IUSR, IIS_IUSRS ou l’utilisateur configuré pour le Pool d’applications est un utilisateur autorisé avec des droits de lecture et exécution. Si aucun de ces utilisateurs sont présentes, ajoutez IUSR en tant qu’utilisateur avec des droits de lecture et exécution.

## <a name="bkmk_webdeploy"></a> Publier et déployer l’application à l’aide de Web Deploy à partir de Visual Studio

[!INCLUDE [deploy-app-web-deploy](../deployment/includes/deploy-app-web-deploy.md)]

En outre, vous devez lire la section sur [résolution des problèmes de ports](#bkmk_openports).

## <a name="bkmk_openports"></a> Résolution des problèmes : Ouvrir les ports requis sur Windows Server

Dans la plupart des configurations, les ports requis sont ouverts par l’installation d’ASP.NET et Web Deploy. Toutefois, vous devrez peut-être vérifier que les ports sont ouverts.

> [!NOTE]
> Sur une machine virtuelle Azure, vous devez ouvrir les ports via la [groupe de sécurité réseau](/azure/virtual-machines/virtual-machines-windows-hero-role#open-port-80). 

Ports requis :

* 80 - requis pour IIS
* 8172 - requis pour Web Deploy déployer l’application à partir de Visual Studio

1. Pour ouvrir un port sur Windows Server, ouvrez le **Démarrer** menu, recherchez **pare-feu Windows avec fonctions avancées de sécurité**.

2. Puis choisissez **règles de trafic entrant > nouvelle règle > Port**. Choisissez **suivant** et sous **ports locaux spécifiques**, entrez le numéro de port, cliquez sur **suivant**, puis **autoriser la connexion**, cliquez sur Suivant, et Ajoutez le nom (**IIS**, **Web Deploy**, ou **msvsmon**) pour la règle de trafic entrant.

    Si vous souhaitez plus d’informations sur la configuration du pare-feu Windows, consultez [configurer le pare-feu Windows pour le débogage distant](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

3. Créer des règles supplémentaires pour les autres ports requis.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous a créé un fichier de paramètres de publication, importé dans Visual Studio et déployé une application ASP.NET sur IIS. Vous pouvez également déployer en important les paramètres de publication.

> [!div class="nextstepaction"]
> [Déployer sur IIS en important les paramètres de publication](../deployment/tutorial-import-publish-settings-iis.md)