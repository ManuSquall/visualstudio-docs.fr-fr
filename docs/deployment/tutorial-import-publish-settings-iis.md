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
ms.openlocfilehash: 907fecd348dba46f6d3375d2d994b04ec1cf1eb5
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2018
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

Un fichier de paramètres de publication (*\*.publishsettings*) est différente de celle d’un profil de publication (*\*.pubxml*) créés dans Visual Studio. Un fichier de paramètres de publication est créé par IIS ou du Service d’applications Azure, ou peuvent être créée manuellement, et il peut ensuite être importé dans Visual Studio.

> [!NOTE]
> Si vous avez besoin copier un profil de publication de Visual Studio (\*.pubxml fichier) à partir d’une installation de Visual Studio à l’autre, vous pouvez trouver le profil de publication,  *\<profilename\>.pubxml*, dans le  *\\< projectname\>\Properties\PublishProfiles* dossier pour les types de projet managés. Pour les sites Web, regardez sous la *\App_Data* dossier. Les profils de publication sont des fichiers XML de MSBuild.

## <a name="prerequisites"></a>Prérequis

* Vous devez disposer de Visual Studio 2017 installé et le **ASP.NET** et **.NET Framework** charge de travail de développement. Pour une application .NET Core, vous devez également le **.NET Core** la charge de travail.

    Si vous n’avez pas encore installé Visual Studio, installez-le gratuitement [ici](http://www.visualstudio.com).

* Pour générer le fichier de paramètres de publication à partir de IIS, vous devez disposer d’un ordinateur exécutant Windows Server 2012 ou Windows Server 2016, et vous devez disposer du rôle serveur Web IIS correctement configuré. ASP.NET 4.5 ou ASP.NET Core doit également être installé. Pour ASP.NET Core, consultez [publication sur IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Pour ASP.NET 4.5, consultez [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

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

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importer les paramètres de publication dans Visual Studio et déployer

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/import-publish-settings-vs.md)]

Après que l’application a été déployé avec succès, il doit démarrer automatiquement. S’il ne démarre pas à partir de Visual Studio, démarrez l’application dans IIS. Pour ASP.NET Core, vous devez vous assurer que le pool d’applications de champ pour le **DefaultAppPool** a la valeur **aucun Code managé**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous a créé un fichier de paramètres de publication, importé dans Visual Studio et déployé une application ASP.NET sur IIS.

> [!div class="nextstepaction"]
> [Présentation du déploiement](../deployment/deploying-applications-services-and-components.md)
