---
title: Publier sur Azure en important des paramètres de publication
description: Créer et importer un profil de publication pour déployer une application à partir de Visual Studio sur Azure App Service
ms.date: 05/07/2018
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: febf742ca7a54a14d8de59c251bb8783cf76370a
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58567878"
---
# <a name="publish-an-application-to-azure-app-service-by-importing-publish-settings-in-visual-studio"></a>Publier une application sur Azure App Service en important des paramètres de publication dans Visual Studio

Vous pouvez utiliser l’outil **Publier** pour importer des paramètres de publication, puis déployer votre application. Dans cet article, nous utilisons des paramètres de publication pour Azure App Service, mais vous pouvez utiliser une procédure similaire pour importer des paramètres de publication [IIS](../deployment/tutorial-import-publish-settings-iis.md). Dans certains scénarios, l’utilisation d’un profil de paramètres de publication peut être plus rapide que la configuration manuelle du déploiement sur le service pour chaque installation de Visual Studio.

Ces étapes s’appliquent aux applications ASP.NET, ASP.NET Core et .NET Core dans Visual Studio. Vous pouvez aussi importer des paramètres de publication pour les applications [Python](../python/publishing-python-web-applications-to-azure-from-visual-studio.md).

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Générer un fichier de paramètres de publication à partir d’Azure App Service
> * Importer le fichier de paramètres de publication dans Visual Studio
> * Déployer l’application sur Azure App Service

Un fichier de paramètres de publication (*\*.publishsettings*) est différent de celui d’un profil de publication (*\*.pubxml*) créé dans Visual Studio. Un fichier de paramètres de publication est créé par Azure App Service et peut être importé dans Visual Studio.

> [!NOTE]
> Si vous voulez simplement copier un profil de publication Visual Studio (fichier *\*.pubxml*) d’une installation de Visual Studio vers une autre, le profil de publication, *\<nom_profil\>.pubxml*, se trouve dans le dossier *\\<nom_projet\>\Properties\PublishProfiles* pour les types de projet gérés. Pour les sites web, regardez sous le dossier *\App_Data*. Les profils de publication sont des fichiers XML MSBuild.

## <a name="prerequisites"></a>Prérequis

::: moniker range=">=vs-2019"

* Visual Studio 2019 et la charge de travail **Développement web et ASP.NET** doivent être installés.

    Si vous n’avez pas encore installé Visual Studio, accédez à la page  [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/)  pour l’installer gratuitement.
::: moniker-end

::: moniker range="vs-2017"

* Visual Studio 2017 et la charge de travail **Développement web et ASP.NET** doivent être installés.

    Si vous n’avez pas encore installé Visual Studio, accédez à la page  [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/)  pour l’installer gratuitement.
::: moniker-end

* Créez un service Azure App Service. Pour des instructions détaillées, consultez [Déployer une application web ASP.NET Core sur Azure avec Visual Studio](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Créer un projet ASP.NET dans Visual Studio

1. Sur l’ordinateur exécutant Visual Studio, créez un projet.

    Choisissez le modèle adéquat. Dans cet exemple, choisissez **Application web ASP.NET (.NET Framework)** ou (pour C# uniquement) **Application web ASP.NET Core**, puis cliquez sur **OK**.

    Si vous ne voyez pas les modèles de projet spécifiés, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Visual Studio Installer est lancé. Installez la charge de travail **Développement web et ASP.NET**.

    Le modèle de projet que vous choisissez (ASP.NET ou ASP.NET Core) doit correspondre à la version installée d’ASP.NET sur le serveur web.

1. Choisissez **MVC** (.NET Framework) ou **Application web (modèle-vue-contrôleur)** (pour .NET Core) et vérifiez que l’option **Aucune authentification** est sélectionnée, puis cliquez sur **OK**.

1. Tapez un nom comme **MyDbgApp**, puis cliquez sur **OK**.

    Visual Studio crée le projet.

1. Choisissez **Générer** > **Générer la solution** pour générer le projet.

## <a name="create-the-publish-settings-file-in-azure-app-service"></a>Créer le fichier de paramètres de publication dans Azure App Service

1. Dans le portail Azure, ouvrez Azure App Service.

1. Cliquez sur **Obtenir le profil de publication** et enregistrez le profil localement.

    ![Obtenir le profil de publication](../deployment/media/tutorial-azure-app-service-get-publish-profile.png)

    Un fichier avec une extension *.publishsettings* a été généré à l’emplacement où vous l’avez enregistré. Le code suivant montre un exemple partiel du fichier (avec une mise en forme plus lisible).

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
    En règle générale, le fichier *.publishsettings précédent contient deux profils de publication que vous pouvez utiliser dans Visual Studio, un pour déployer à l’aide de Web Deploy et l’autre pour déployer à l’aide de FTP. Le code précédent affiche le profil Web Deploy. Les deux profils sont importés quand vous importez le profil.

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importer les paramètres de publication dans Visual Studio et déployer

[!INCLUDE [import publish settings](../deployment/includes/import-publish-settings-vs.md)]

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez créé un fichier de paramètres de publication, l’avez importé dans Visual Studio et avez déployé une application ASP.NET sur Azure App Service. Consultez une vue d’ensemble des options de publication dans Visual Studio.

> [!div class="nextstepaction"]
> [Présentation du déploiement](../deployment/deploying-applications-services-and-components.md)
