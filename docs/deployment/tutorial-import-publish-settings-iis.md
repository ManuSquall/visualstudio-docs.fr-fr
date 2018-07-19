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
ms.openlocfilehash: e6df935578955d3c72b6f4fa61efdf614229bca0
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38808463"
---
# <a name="publish-an-application-to-iis-by-importing-publish-settings-in-visual-studio"></a>Publier une application à IIS en important les paramètres de publication dans Visual Studio

Vous pouvez utiliser la **publier** outil permettant d’importer les paramètres de publication, puis déployer votre application. Dans cet article, nous utilisons des paramètres pour IIS de publication, mais vous pouvez utiliser une procédure similaire pour importer des paramètres de publication pour [Azure App Service](../deployment/tutorial-import-publish-settings-azure.md). Dans certains scénarios, l’utilisation de publier une version de profil des paramètres peut être plus rapide que de configurer manuellement le déploiement vers IIS pour chaque installation de Visual Studio.

Ces étapes s’appliquent aux applications ASP.NET, ASP.NET Core et .NET Core dans Visual Studio. Les étapes correspondent à Visual Studio 2017 version 15.6.

Dans ce didacticiel, vous allez effectuer les actions suivantes :

> [!div class="checklist"]
> * Configurer IIS pour que vous pouvez générer un fichier de paramètres de publication
> * Créer un fichier de paramètres de publication
> * Importer le fichier de paramètres de publication dans Visual Studio
> * Déployer l’application sur IIS

Un fichier de paramètres de publication (*\*.publishsettings*) est différente de celle d’un profil de publication (*\*.pubxml*) créés dans Visual Studio. Un fichier de paramètres de publication est créé par IIS ou Azure App Service, ou peuvent être créée manuellement, et il peut être importé dans Visual Studio.

> [!NOTE]
> Si vous souhaitez simplement copier un profil de publication de Visual Studio (\*fichier .pubxml) à partir d’une installation de Visual Studio à l’autre, vous pouvez trouver le profil de publication,  *\<profilename\>.pubxml*, dans le  *\\< nom_projet\>\Properties\PublishProfiles* dossier pour les types de projet managé. Pour les sites Web, regardez sous le *\App_Data* dossier. Les profils de publication sont des fichiers XML de MSBuild.

## <a name="prerequisites"></a>Prérequis

* Vous devez disposer de Visual Studio 2017 est installé et le **ASP.NET** et **.NET Framework** charge de travail de développement. Pour une application .NET Core, vous devez également le **.NET Core** charge de travail.

    Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

* Pour générer le fichier de paramètres de publication à partir d’IIS, vous devez disposer d’un ordinateur exécutant Windows Server 2012 ou Windows Server 2016, et vous devez disposer du rôle de serveur Web IIS correctement configuré. ASP.NET 4.5 ou ASP.NET Core doit également être installé. Pour ASP.NET Core, consultez [publication sur IIS](/aspnet/core/publishing/iis?tabs=aspnetcore2x#iis-configuration). Pour ASP.NET 4.5, consultez [IIS 8.0 à l’aide de ASP.NET 3.5 et ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

## <a name="create-a-new-aspnet-project-in-visual-studio"></a>Créer un nouveau projet ASP.NET dans Visual Studio

1. Sur l’ordinateur exécutant Visual Studio, choisissez **fichier** > **nouveau projet**.

1. Sous **Visual C#** ou **Visual Basic**, choisissez **Web**, puis dans le volet central **Application Web ASP.NET (.NET Framework)** ou (c# uniquement) **Application Web ASP.NET Core**, puis cliquez sur **OK**.

    Si vous ne voyez pas les modèles de projet spécifiée, cliquez sur le **ouvrir Visual Studio Installer** lien dans le volet gauche de la **nouveau projet** boîte de dialogue. Visual Studio Installer est lancé. Consultez les conditions préalables dans cet article pour identifier les charges de travail Visual Studio requis, que vous devez installer.

1. Choisissez **MVC** (.NET Framework) ou **l’Application Web (Model-View-Controller)** (pour .NET Core) et assurez-vous que l’option **aucune authentification** est sélectionnée, puis cliquez sur **OK**.

1. Tapez un nom tel que **MyWebApp** et cliquez sur **OK**.

    Visual Studio crée le projet.

1. Choisissez **Build** > **générer la Solution** pour générer le projet.

## <a name="install-and-configure-web-deploy-on-windows-server"></a>Installer et configurer Web Deploy sur Windows Server

[!INCLUDE [install-web-deploy-with-hosting-server](../deployment/includes/install-web-deploy-with-hosting-server.md)]

## <a name="create-the-publish-settings-file-in-iis-on-windows-server"></a>Créer le fichier de paramètres de publication dans IIS sur Windows Server

[!INCLUDE [create-publish-settings-iis](../deployment/includes/create-publish-settings-iis.md)]

## <a name="import-the-publish-settings-in-visual-studio-and-deploy"></a>Importer les paramètres de publication dans Visual Studio et déployer

[!INCLUDE [import-publish-settings](../deployment/includes/import-publish-settings-vs.md)]

Une fois que l’application se déploie correctement, il doit démarrer automatiquement. S’il ne démarre pas à partir de Visual Studio, démarrez l’application dans IIS. Pour ASP.NET Core, vous devez vous assurer que le pool d’applications de champ pour le **DefaultAppPool** a la valeur **aucun Code managé**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce didacticiel, vous créé un fichier de paramètres de publication importé dans Visual Studio et déployé une application ASP.NET sur IIS. Vous souhaiterez peut-être une vue d’ensemble des autres options de publication dans Visual Studio.

> [!div class="nextstepaction"]
> [Présentation du déploiement](../deployment/deploying-applications-services-and-components.md)
