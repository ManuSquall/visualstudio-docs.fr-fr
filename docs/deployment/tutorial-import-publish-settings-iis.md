---
title: Publier sur IIS en important les paramètres de publication
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to IIS
ms.date: 05/07/2018
ms.technology: vs-ide-deployment
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1db8ca68453cff105f2bbefcd384b8afa9efea9d
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publier une application à IIS à l’importation de paramètres de publication dans Visual Studio

Vous pouvez utiliser la **publier** outil pour importer des paramètres de publication, puis déployer votre application. Dans cet article, nous utilisons paramètres de publication pour IIS, mais vous pouvez utiliser des étapes similaires pour importer des paramètres de publication pour [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). Dans certains scénarios, l’utilisation de publier une version de profil de paramètres peut être plus rapide que la configuration manuelle de déploiement sur le serveur IIS pour chaque installation de Visual Studio.

Ces étapes s’appliquent aux applications ASP.NET et ASP.NET Core .NET Core dans Visual Studio. Les étapes correspondent à Visual Studio 2017 version 15,6.

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Configurer IIS afin que vous pouvez générer un fichier de paramètres de publication
> * Créer un fichier de paramètres de publication
> * Importer le fichier de paramètres de publication dans Visual Studio
> * Déployer l’application sur IIS

Un fichier de paramètres de publication (\*.publishsettings) est différente de celle d’un profil de publication (\*.pubxml) créé dans Visual Studio. Un fichier de paramètres de publication est créé par IIS ou du Service d’applications Azure, ou peuvent être créée manuellement, et il peut ensuite être importé dans Visual Studio.

> [!NOTE]
> Si vous avez besoin copier un profil de publication de Visual Studio (\*.pubxml fichier) à partir d’une installation de Visual Studio à l’autre, vous pouvez trouver le profil de publication,  *\<profilename\>.pubxml*, dans le  *\\< projectname\>\Properties\PublishProfiles* dossier pour les types de projet managés. Pour les sites Web, regardez sous la *\App_Data* dossier. Les profils de publication sont des fichiers XML de MSBuild.

## <a name="prerequisites"></a>Prérequis

* Vous devez disposer de Visual Studio est installé et le **ASP.NET** et **.NET Framework** charge de travail de développement. Pour une application .NET Core, vous devez également le **.NET Core** la charge de travail.

    Si vous n’avez pas encore installé Visual Studio, installez-le gratuitement [ici](http://www.visualstudio.com).

    Les étapes décrites dans cet article sont basés sur Visual Studio 2017

* Pour générer le fichier de paramètres de publication à partir de IIS, vous devez disposer d’un autre ordinateur exécutant Windows Server 2012 avec le rôle de serveur Web de IIS 8.0 correctement configuré et soit ASP.NET 4.5 ou ASP.NET Core installé. Pour ASP.NET Core, consultez [publication sur IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Pour ASP.NET 4.5, consultez [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Créer un nouveau projet ASP.NET dans Visual Studio

1. Sur l’ordinateur exécutant Visual Studio, choisissez **fichier > Nouveau projet**.

1. Sous **Visual C#** ou **Visual Basic**, choisissez **Web**, puis dans le volet central, choisissez soit **ASP.NET Web Applications (.NET Framework)** ou (c# uniquement) **Application ASP.NET Core Web**, puis cliquez sur **OK**.

    Si vous ne voyez pas les modèles de projet spécifié, cliquez sur le **ouvrir Visual Studio Installer** lien dans le volet gauche de la **nouveau projet** boîte de dialogue. Visual Studio Installer est lancé. Consultez les conditions préalables dans cet article pour identifier les charges de travail Visual Studio requis, que vous devez installer.

1. Choisissez **MVC** (.NET Framework) ou **l’Application Web (Model-View-Controller)** (pour .NET Core) et vous assurer que **aucune authentification** est sélectionné, puis cliquez sur **OK**.

1. Tapez un nom tel que **MyWebApp** et cliquez sur **OK**.

    Visual Studio crée le projet.

1. Choisissez **Générer > Générer la Solution** pour générer le projet.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Installer et configurer Web Deploy sur Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Créer le fichier de paramètres de publication dans IIS sur Windows Server

1. Dans IIS, cliquez sur le **Site Web par défaut**, choisissez **déployer** > **configuration Web déployer de la publication**.

    ![Configurer la configuration de déploiement Web](../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. Dans le **configuration Web déployer de la publication** boîte de dialogue zone, examinez les paramètres.

1. Cliquez sur **le programme d’installation**.

    Dans le **résultats** Panneau de configuration, la sortie montre que les droits d’accès ont été accordée à l’utilisateur spécifié et qu’un fichier avec un *.publishsettings* extension de fichier a été générée à l’emplacement indiqué dans le boîte de dialogue.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    Selon votre configuration de Windows Server et les services IIS, vous verrez des valeurs différentes. Voici quelques détails sur les valeurs que vous voyez :

    * Le *msdeploy.axd* fichier référencé dans le `publishUrl` attribut est un fichier de gestionnaire HTTP générées dynamiquement pour Web Deploy. (Pour des tests, `http://myhostname:8172` fonctionne généralement ainsi.)
    * Le `publishUrl` port est généralement défini sur le port 8172, qui est la valeur par défaut pour Web Deploy.
    * Le `destinationAppUrl` port est généralement défini sur le port 80, qui est la valeur par défaut pour IIS.
    * Si vous ne parvenez pas à se connecter à l’hôte distant dans Visual Studio en utilisant le nom d’hôte (dans les étapes suivantes), testez l’adresse IP à la place du nom d’hôte.

    > [!NOTE]
    > Si vous publiez sur IIS qui s’exécute sur une machine virtuelle Azure, les ports IIS et Web Deploy doivent être ouvert dans le groupe de sécurité réseau. Pour plus d’informations, consultez [installer et exécuter IIS](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic).

1. Copiez ce fichier sur l’ordinateur sur lequel vous exécutez Visual Studio.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importer les paramètres de publication dans Visual Studio et déployer

1. Sur l’ordinateur où vous ouvrir le projet ASP.NET dans Visual Studio, cliquez sur le projet dans l’Explorateur de solutions, puis choisissez **publier**.

1. Si vous avez déjà configuré des profils de publication, le **publier** volet s’affiche. Cliquez sur **créer nouveau profil**.

1. Dans le **choisir une cible de publication** boîte de dialogue, cliquez sur **importer un profil**.

    ![Choisissez publier](../deployment/media/tutorial-publish-tool-import-profile.png)

1. Accédez à l’emplacement du fichier de paramètres de publication que vous avez créé dans la section précédente.

1. Dans le **importation publier un fichier de paramètres** boîte de dialogue, accédez à et sélectionnez le profil que vous avez créé dans la section précédente, puis cliquez sur **ouvrir**.

    Visual Studio lance le processus de déploiement, et la fenêtre Sortie affiche la progression et les résultats.

    Si vous obtenez un déploiement de toutes les erreurs, cliquez sur **paramètres** pour modifier les paramètres. Modifier les paramètres et cliquez sur **Validate** pour tester les nouveaux paramètres.

    ![Modifier les paramètres dans l’outil de publication](../deployment/media/tutorial-configure-publish-settings-in-tool.png)

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous a créé un fichier de paramètres de publication, importé dans Visual Studio et déployé une application ASP.NET sur IIS.

> [!div class="nextstepaction"]
> [Présentation du déploiement](../deployment/deploying-applications-services-and-components.md)
