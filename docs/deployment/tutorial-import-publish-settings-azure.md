---
title: Publier sur Azure en important les paramètres de publication
ms.custom: Create and import a publishing profile to deploy an application from Visual Studio to Azure App Service
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
ms.openlocfilehash: 2cf6c17f3017bb1021423b19b32b36749fe0744d
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2018
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publier une application de Service d’applications Azure en important des paramètres de publication dans Visual Studio

Vous pouvez utiliser la **publier** outil pour importer des paramètres de publication, puis déployer votre application. Dans cet article, nous utilisons les paramètres pour Azure App Service de publication, mais vous pouvez utiliser des étapes similaires pour importer les paramètres à partir de publication [IIS](../deployment/tutorial-import-publish-settings-iis.md). Dans certains scénarios, l’utilisation de publier une version de profil de paramètres peut être plus rapide que la configuration manuelle de déploiement pour le service pour chaque installation de Visual Studio.

Ces étapes s’appliquent aux applications ASP.NET et ASP.NET Core .NET Core dans Visual Studio. Vous pouvez également importer des paramètres de publication pour [Python](/visualstudio/python/publishing-python-web-applications-to-azure-from-visual-studio) applications. Les étapes correspondent à Visual Studio 2017 version 15,6.

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Générer un fichier de paramètres de publication à partir du Service d’applications Azure
> * Importer le fichier de paramètres de publication dans Visual Studio
> * Déployer l’application dans Azure App Service

Un fichier de paramètres de publication (*\*.publishsettings*) est différente de celle d’un profil de publication (*\*.pubxml*) créés dans Visual Studio. Un fichier de paramètres de publication est créé par le Service d’applications Azure, et il peut ensuite être importé dans Visual Studio.

> [!NOTE]
> Si vous avez besoin copier un profil de publication de Visual Studio (*\*.pubxml* fichier) à partir d’une installation de Visual Studio à l’autre, vous pouvez trouver le profil de publication,  *\<profilename\>.pubxml*, dans le  *\\< projectname\>\Properties\PublishProfiles* dossier pour les types de projet managés. Pour les sites Web, regardez sous la *\App_Data* dossier. Les profils de publication sont des fichiers XML de MSBuild.

## <a name="prerequisites"></a>Prérequis

* Vous devez disposer de Visual Studio 2017 installé et le **ASP.NET** et **.NET Framework** charge de travail de développement. Pour une application .NET Core, vous devez également le **.NET Core** la charge de travail.

    Si vous n’avez pas encore installé Visual Studio, installez-le gratuitement [ici](http://www.visualstudio.com).

* Créer un Service d’application Azure. Pour obtenir des instructions détaillées, consultez [déployer une application de web ASP.NET Core pour Azure à l’aide de Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs). 

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Créer un nouveau projet ASP.NET dans Visual Studio

1. Sur l’ordinateur exécutant Visual Studio, choisissez **fichier > Nouveau projet**.

1. Sous **Visual C#** ou **Visual Basic**, choisissez **Web**, puis dans le volet central, choisissez soit **ASP.NET Web Applications (.NET Framework)** ou (c# uniquement) **Application ASP.NET Core Web**, puis cliquez sur **OK**.

    Si vous ne voyez pas les modèles de projet spécifié, cliquez sur le **ouvrir Visual Studio Installer** lien dans le volet gauche de la **nouveau projet** boîte de dialogue. Visual Studio Installer est lancé. Consultez les conditions préalables dans cet article pour identifier les charges de travail Visual Studio requis, que vous devez installer.

1. Choisissez **MVC** (.NET Framework) ou **l’Application Web (Model-View-Controller)** (pour .NET Core) et vous assurer que **aucune authentification** est sélectionné, puis cliquez sur **OK**.

1. Tapez un nom tel que **MyWebApp** et cliquez sur **OK**.

    Visual Studio crée le projet.

1. Choisissez **Générer > Générer la Solution** pour générer le projet.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Créer le fichier de paramètres de publication dans Azure App Service

1. Dans le portail Azure, ouvrez le Service d’applications Azure.

1. Cliquez sur **obtenir le profil de publication** et enregistrez le profil local.

    ![Obtenir le profil de publication](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Un fichier avec un *.publishsettings* extension de fichier a été générée à l’emplacement où vous l’avez enregistré. Le code suivant montre un exemple partiel du fichier (dans une mise en forme plus lisible).

    ```xml
    <publishData>
      <publishProfile
        profileName="DeployASPDotNetCore - Web Deploy"
        publishMethod="MSDeploy"
        publishUrl="deployaspdotnetcore.scm.azurewebsites.net:443"
        msdeploySite="DeployASPDotNetCore"
        userName="$DeployASPDotNetCore"
        userPWD="abcdefghijklmnopqrstuzwxyz"
        destinationAppUrl="http://deployaspdotnetcore20180508031824.azurewebsites.net"
        SQLServerDBConnectionString=""
        mySQLDBConnectionString=""
        hostingProviderForumLink=""
        controlPanelLink="http://windows.azure.com"
        webSystem="WebSites">
        <databases />
      </publishProfile>
    </publishData>
    ```
    En règle générale, le fichier *.publishsettings précédent contient deux profils de publication que vous pouvez utiliser dans Visual Studio, un déploiement à l’aide de Web Deploy et un déploiement à l’aide de FTP. Le code précédent montre le profil de déploiement Web. Les deux profils seront importés ultérieurement lorsque vous importez le profil.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importer les paramètres de publication dans Visual Studio et déployer

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous a créé un fichier de paramètres de publication importé dans Visual Studio et déployé une application ASP.NET pour le Service d’applications Azure.

> [!div class="nextstepaction"]
> [Présentation du déploiement](../deployment/deploying-applications-services-and-components.md)
