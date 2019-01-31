---
title: Publier sur IIS en important des paramètres de publication
description: Créer et importer un profil de publication pour déployer une application de Visual Studio sur IIS
ms.date: 05/07/2018
ms.topic: tutorial
helpviewer_keywords:
- deployment, publish settings
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 064eb9f57db538df4cae32777e9ac61359ddea4d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026878"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publier une application sur IIS en important des paramètres de publication dans Visual Studio

Vous pouvez utiliser l’outil **Publier** pour importer des paramètres de publication, puis déployer votre application. Dans cet article, nous utilisons des paramètres de publication pour IIS, mais vous pouvez utiliser une procédure similaire pour importer des paramètres de publication [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). Dans certains scénarios, l’utilisation d’un profil de paramètres de publication peut être plus rapide que la configuration manuelle du déploiement sur IIS pour chaque installation de Visual Studio.

Ces étapes s’appliquent aux applications ASP.NET, ASP.NET Core et .NET Core dans Visual Studio. Les étapes correspondent à Visual Studio 2017 version 15.6.

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

* Vous devez avoir installé Visual Studio 2017 et la charge de travail de développement **ASP.NET** et **NET Framework**. Pour une application .NET Core, vous avez aussi besoin de la charge de travail **NET Core**.

    Si vous n’avez pas encore installé Visual Studio, accédez à la page  [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)  pour l’installer gratuitement.

* Pour générer le fichier de paramètres de publication à partir d’IIS, vous devez avoir un ordinateur exécutant Windows Server 2012 ou Windows Server 2016, et avoir correctement configuré le rôle serveur web IIS. ASP.NET 4.5 ou ASP.NET Core doit également être installé. Pour ASP.NET Core, consultez [Publication sur IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Pour ASP.NET 4.5, consultez [IIS 8.0 avec ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Créer un projet ASP.NET dans Visual Studio

1. Sur l’ordinateur exécutant Visual Studio, choisissez **Fichier** > **Nouveau projet**.

1. Sous **Visual C#**  ou **Visual Basic**, choisissez **Web**, puis dans le volet central choisissez **Application web ASP.NET (.NET Framework)** ou (C# uniquement) **Application web ASP.NET Core**, puis cliquez sur **OK**.

    Si vous ne voyez pas les modèles de projet spécifiés, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Visual Studio Installer est lancé. Consultez les prérequis dans cet article pour identifier les charges de travail Visual Studio à installer.

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
