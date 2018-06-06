---
title: Publier sur un site Web - Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/22/2017
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f722dcc4ada5643f9de3342b85469fa667d4b7c
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34766550"
---
# <a name="publish-a-web-app-or-a-net-core-app-to-a-web-site-using-the-visual-studio-publish-tool"></a>Publier une application web ou une application .NET Core sur un site web à l’aide de l’outil de publication de Visual Studio

Vous pouvez utiliser la **publier** outil pour publier des applications ASP.NET à un site Web.

Ces étapes s’appliquent aux applications ASP.NET, ASP.NET Core, .NET Core et Python dans Visual Studio. Pour Node.js, les étapes sont prises en charge, mais l’interface utilisateur est différente. Pour Node.js, les étapes sont pris en charge, mais l’interface utilisateur est différent.

## <a name="prerequisites"></a>Prérequis

* Vous devez disposer de Visual Studio 2017 installé et le **ASP.NET et le développement web** la charge de travail et. **Développement de bureau NET** la charge de travail. Pour une application .NET Core, vous devez le. **NET Core** la charge de travail.

    Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

## <a name="create-a-new-project"></a>Créer un nouveau projet 

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau projet**.

1. Sous **Visual C#** ou **Visual Basic**, choisissez **Web**, puis dans le volet central, choisissez soit **ASP.NET Web Applications (.NET Framework)** ou (c# uniquement) **Application ASP.NET Core Web**, puis cliquez sur **OK**.

1. Choisissez **MVC** (ou choisissez **l’Application Web (Model-View-Controller)** pour .NET Core), assurez-vous que **aucune authentification** est sélectionné, puis cliquez sur **OK** .

1. Tapez un nom tel que **MyWebApp** et cliquez sur **OK**.

    Visual Studio crée le projet.

1. Choisissez **Générer > Générer la Solution** pour générer le projet.

## <a name="publish-to-a-web-site"></a>Publier sur un site web

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier**.

    ![Choisissez publier](../deployment/media/quickstart-publish-aspnet.png "choisissez Publier")

1. Si vous avez déjà configuré des profils de publication, le **publier** volet s’affiche. Cliquez sur **créer nouveau profil**.

1. Dans le **choisir une cible de publication** boîte de dialogue, choisissez **IIS, FTP, etc**.

    ![Choisissez IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png "IIS de choisir, FTP, etc..")

1. Cliquez sur **Publier**.

    Le profil de paramètres ouvre la boîte de dialogue de publication.

    ![Choisissez le dossier](../deployment/media/quickstart-publish-settings-web.png "dossier")

1. Dans le **méthode de publication** champ, choisissez une méthode comme **Web Deploy** ou **FTP**.

    Ensuite, les paramètres que vous voyez correspondent à votre méthode de publication. Web Deploy simplifie le déploiement d’applications Web et sites Web aux serveurs IIS et doit être installé en tant qu’application sur le serveur. Utilisez le [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx) pour l’installer.

1. Configurez les paramètres requis pour la méthode de publication, cliquez sur **valider la connexion**.

    Si le serveur ou la cible est disponible et que vos paramètres sont corrects, vous verrez un message indiquant que la connexion est validé, et vous êtes prêt à publier.

    ![Valider votre connexion](../deployment/media/quickstart-publish-web-deploy.png "valider votre connexion")

1. Si vous souhaitez configurer d’autres paramètres de déploiement, cliquez sur **paramètres**.

    Vous pouvez configurer des options telles que s’il faut déployer une configuration Debug ou Release, puis cliquez sur **enregistrer**. Si vous effectuez un débogage à distance, une configuration de débogage est requise.

1. Pour publier, cliquez sur **publier**.

    La fenêtre Sortie affiche les résultats et la progression du déploiement.

## <a name="next-steps"></a>Étapes suivantes

Dans ce démarrage rapide, vous avez appris à utiliser Visual Studio pour créer un profil de publication. Vous pouvez également configurer une publication de profil en important les paramètres de publication.

> [!div class="nextstepaction"]
> [Importer des paramètres de publication et déployer sur IIS](tutorial-import-publish-settings-iis.md)
