---
title: Publier sur un site Web - Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/22/2017
ms.technology:
- vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 43b6bacc45d78d1d246f6a91d13549ccc96b276a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="publish-a-web-app-or-a-net-core-app-to-a-web-site-using-the-visual-studio-publish-tool"></a>Publier une application web ou une application .NET Core sur un site web à l’aide de l’outil de publication de Visual Studio

Vous pouvez utiliser la **publier** outil pour publier des applications ASP.NET à un site Web.

Ces étapes s’appliquent aux applications ASP.NET, ASP.NET Core, .NET Core et Python dans Visual Studio. Pour Node.js, les étapes sont prises en charge, mais l’interface utilisateur est différente. Pour Node.js, les étapes sont pris en charge, mais l’interface utilisateur est différent.

## <a name="create-a-new-project"></a>Créer un nouveau projet 

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau projet**.

1. Sous **Visual C#** ou **Visual Basic**, choisissez **Web**, puis dans le volet central, choisissez soit **ASP.NET Web Applications (.NET Framework)**ou (c# uniquement) **Application ASP.NET Core Web**, puis cliquez sur **OK**.

1. Choisissez **MVC**, assurez-vous que **aucune authentification** est sélectionné, puis cliquez sur **OK**.

1. Tapez un nom tel que **MyWebApp** et cliquez sur **OK**.

    Visual Studio crée le projet.

1. Choisissez **Générer > Générer la Solution** pour générer le projet.

## <a name="publish-to-a-web-site"></a>Publier sur un site web

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier**.

    ![Choisissez publier](../deployment/media/quickstart-publish-aspnet.png "choisissez Publier")

1. Dans le **publier** volet, choisissez **IIS, FTP, etc**.

    ![Choisissez IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png "IIS de choisir, FTP, etc..")

1. Cliquez sur **Publier**.

    Le profil de paramètres ouvre la boîte de dialogue de publication.

    ![Choisissez le dossier](../deployment/media/quickstart-publish-settings-web.png "dossier")

1. Dans le **méthode de publication** champ, choisissez une méthode comme **Web Deploy** ou **FTP**.

    Ensuite, les paramètres que vous voyez correspondent à votre méthode de publication.

1. Configurez les paramètres requis pour la méthode de publication, cliquez sur **valider la connexion**.

    Si le serveur ou la cible est disponible et que vos paramètres sont corrects, vous verrez un message indiquant que la connexion est validé, et vous êtes prêt à publier.

    ![Valider votre connexion](../deployment/media/quickstart-publish-web-deploy.png "valider votre connexion")

1. Si vous souhaitez configurer d’autres paramètres de déploiement, cliquez sur **paramètres**.

    Vous pouvez configurer des options telles que s’il faut déployer une configuration Debug ou Release, puis cliquez sur **enregistrer**. Si vous effectuez un débogage à distance, une configuration de débogage est requise.

1. Pour publier, cliquez sur **publier**.

    La fenêtre Sortie affiche les résultats et la progression du déploiement.

## <a name="next-steps"></a>Étapes suivantes

- [Déployer ASP.NET sur IIS](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45)
