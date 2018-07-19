---
title: Publier sur un site Web
ms.custom: ''
ms.date: 06/22/2018
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
ms.openlocfilehash: 036d7549995f79808142c3a0a64e7e5f2075df2c
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077501"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publier une application Web sur un site web à l’aide de Visual Studio

Vous pouvez utiliser la **publier** outil pour publier des applications ASP.NET, ASP.NET Core, .NET Core et Python à un site Web à partir de Visual Studio. Pour Node.js, les étapes sont pris en charge, mais l’interface utilisateur est différente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="publish-to-a-web-site"></a>Publier sur un site Web

1. Dans l’Explorateur de solutions, cliquez sur le projet et choisissez **publier** (ou utilisez le **Build** > **publier** élément de menu).

    ![La commande Publier sur le menu contextuel du projet dans l’Explorateur de solutions](../deployment/media/quickstart-publish.png "choisissez Publier")

1. Si vous avez déjà configuré des profils de publication, le **publier** volet s’affiche. Sélectionnez **créer nouveau profil**.

1. Dans le **choisir une cible de publication** boîte de dialogue, choisissez **IIS, FTP, etc**.

    ![Choisissez IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png "choisir de IIS, FTP, etc..")

1. Sélectionnez **Publier**. Le profil des paramètres ouvre la boîte de dialogue de publication.

    ![Choisissez le dossier](../deployment/media/quickstart-publish-settings-web.png "choisir le dossier")

1. Dans le **méthode de publication** champ, choisissez une méthode comme **Web Deploy** ou **FTP**. Ensuite, les paramètres que vous voyez correspondent à votre méthode de publication. Web Deploy simplifie le déploiement d’applications Web et sites Web sur des serveurs IIS et doit être installé en tant qu’application sur le serveur. Utilisez le [le programme d’installation de Web platform](https://www.microsoft.com/web/downloads/platform.aspx) pour l’installer.

1. Configurer les paramètres requis pour la méthode de publication et sélectionnez **valider la connexion**. Si le serveur ou la cible est disponible et vos paramètres sont corrects, un message qui indique la connexion est validé, et vous êtes prêt à publier.

    ![Valider votre connexion](../deployment/media/quickstart-publish-web-deploy.png "valider votre connexion")

1. Sélectionnez **paramètres** pour configurer d’autres paramètres de déploiement, comme s’il faut déployer une configuration Debug ou Release, puis sélectionnez **enregistrer**. Si vous déboguez à distance, une configuration Debug est requise.

1. Pour publier, sélectionnez **publier**. La fenêtre Sortie affiche les résultats et la progression du déploiement.

## <a name="next-steps"></a>Étapes suivantes

Dans ce démarrage rapide, vous avez appris à utiliser Visual Studio pour créer un profil de publication. Vous pouvez également configurer une publication profil en important les paramètres de publication.

> [!div class="nextstepaction"]
> [Importer des paramètres de publication et déployer sur IIS](tutorial-import-publish-settings-iis.md)
