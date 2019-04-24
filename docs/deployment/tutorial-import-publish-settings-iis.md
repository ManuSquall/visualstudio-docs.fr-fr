---
title: Publier sur IIS en important des paramètres de publication
description: Créer et importer un profil de publication pour déployer une application de Visual Studio sur IIS
ms.date: 01/31/2019
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6b0c4f870de455238c02f5dbecbc0c5d56dfbc9
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2019
ms.locfileid: "58567826"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publier une application sur IIS en important des paramètres de publication dans Visual Studio

Vous pouvez utiliser l’outil **Publier** pour importer des paramètres de publication, puis déployer votre application. Dans cet article, nous utilisons des paramètres de publication pour IIS, mais vous pouvez utiliser une procédure similaire pour importer des paramètres de publication [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). Dans certains scénarios, l’utilisation d’un profil de paramètres de publication peut être plus rapide que la configuration manuelle du déploiement sur IIS pour chaque installation de Visual Studio.

Ces étapes s’appliquent aux applications ASP.NET, ASP.NET Core et .NET Core dans Visual Studio.

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Configurer IIS pour pouvoir générer un fichier de paramètres de publication
> * Créer un fichier de paramètres de publication
> * Importer le fichier de paramètres de publication dans Visual Studio
> * Déployer l’application sur IIS

Un fichier de paramètres de publication (*\*.publishsettings*) est différent de celui d’un profil de publication (*\*.pubxml*) créé dans Visual Studio. Un fichier de paramètres de publication est créé par IIS ou Azure App Service, il peut aussi être créé manuellement, pour ensuite être importé dans Visual Studio.

> [!NOTE]
> Si vous voulez simplement copier un profil de publication Visual Studio (fichier \*.pubxml) d’une installation de Visual Studio vers une autre, le profil de publication, *\<nom_profil\>.pubxml*, se trouve dans le dossier *\\<nom_projet\>\Properties\PublishProfiles* pour les types de projet gérés. Pour les sites web, regardez sous le dossier *\App_Data*. Les profils de publication sont des fichiers XML MSBuild.

## <a name="prerequisites"></a>Prérequis

::: moniker range=">=vs-2019"

* Visual Studio 2019 et la charge de travail **Développement web et ASP.NET** doivent être installés.

    Si vous n’avez pas encore installé Visual Studio, accédez à la page  [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/)  pour l’installer gratuitement.
::: moniker-end

::: moniker range="vs-2017"

* Visual Studio 2017 et la charge de travail **Développement web et ASP.NET** doivent être installés.

    Si vous n’avez pas encore installé Visual Studio, accédez à la page  [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/)  pour l’installer gratuitement.
::: moniker-end

* Sur votre serveur, vous devez exécuter Windows Server 2012 ou Windows Server 2016, et le [rôle serveur web IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) doit être correctement installé (nécessaire pour générer le fichier de paramètres de publication (*\*.publishsettings*)). ASP.NET 4.5 ou ASP.NET Core doit également être installé sur le serveur. Pour configurer ASP.NET 4.5, consultez [IIS 8.0 avec ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Pour configurer ASP.NET Core, consultez [Héberger ASP.NET Core sur Windows avec IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Créer un projet ASP.NET dans Visual Studio

1. Sur l’ordinateur exécutant Visual Studio, créez un projet.

    Choisissez le modèle adéquat. Dans cet exemple, choisissez **Application web ASP.NET (.NET Framework)** ou (pour C# uniquement) **Application web ASP.NET Core**, puis cliquez sur **OK**.

    Si vous ne voyez pas les modèles de projet spécifiés, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Visual Studio Installer est lancé. Installez la charge de travail **Développement web et ASP.NET**.

    Le modèle de projet que vous choisissez (ASP.NET ou ASP.NET Core) doit correspondre à la version installée d’ASP.NET sur le serveur web.

1. Choisissez **MVC** (.NET Framework) ou **Application web (modèle-vue-contrôleur)** (pour .NET Core) et vérifiez que l’option **Aucune authentification** est sélectionnée, puis cliquez sur **OK**.

1. Tapez un nom comme **MyDbgApp**, puis cliquez sur **OK**.

    Visual Studio crée le projet.

1. Choisissez **Générer** > **Générer la solution** pour générer le projet.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Installer et configurer Web Deploy sur Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Créer le fichier de paramètres de publication dans IIS sur Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importer les paramètres de publication dans Visual Studio et déployer

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Une fois l’application déployée, elle doit démarrer automatiquement. Si elle ne démarre pas à partir de Visual Studio, démarrez l’application dans IIS. Pour ASP.NET Core, vous devez vérifier que le champ Pool d’applications pour **DefaultAppPool** est défini sur **Aucun code managé**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez créé un fichier de paramètres de publication, l’avez importé dans Visual Studio et avez déployé une application ASP.NET sur IIS. Consultez une vue d’ensemble des autres options de publication dans Visual Studio.

> [!div class="nextstepaction"]
> [Présentation du déploiement](../deployment/deploying-applications-services-and-components.md)
