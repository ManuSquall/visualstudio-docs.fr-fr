---
title: Publier sur un site web
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, website
ms.assetid: fc82b1f1-d342-4b82-9a44-590479f0a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae1d142058b2f655bb55e5140a6ad6ac5f119742
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263501"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publier une application web sur un site web à l’aide de Visual Studio

Vous pouvez utiliser l’outil **Publier** pour publier des applications ASP.NET, ASP.NET Core, .NET Core et Python sur un site web à partir de Visual Studio. Pour Node.js, les étapes sont prises en charge, mais l’interface utilisateur est différente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Si vous devez publier une application de poste de travail Windows sur un partage de fichiers réseau, consultez [Déployer une application de poste de travail avec ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# ou Visual Basic). Pour C++/ CLR, consultez [Déployer une application native avec ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) ou, pour C/C++, consultez [Déployer une application native avec un projet d’installation](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Publier sur un site web

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier** (ou utilisez l’élément de menu **Générer** > **Publier**).

    ![Commande Publier du menu contextuel du projet dans l’Explorateur de solutions](../deployment/media/quickstart-publish.png "Choisissez Publier")

1. Si vous avez déjà configuré des profils de publication, le volet **Publier** s’affiche. Cliquez sur **Créer un profil**.

1. Dans la boîte de dialogue **Choisir une cible de publication**, choisissez **IIS, FTP, etc**.

    ![Choisir IIS, FTP, etc.](../deployment/media/quickstart-publish-iis-ftp.png "Choisir IIS, FTP, etc.")

1. Sélectionnez **Publier**. La boîte de dialogue des paramètres de publication du profil s’ouvre.

    ![Choisir un dossier](../deployment/media/quickstart-publish-settings-web.png "Choisir un dossier")

1. Dans le champ **Méthode de publication**, choisissez la méthode **Web Deploy** ou **FTP**. Les paramètres que vous voyez ensuite correspondent à votre méthode de publication. Web Deploy simplifie le déploiement d’applications web et de sites web sur des serveurs IIS, et doit être installé comme une application sur le serveur. Utilisez [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx) pour l’installer.

1. Configurez les paramètres nécessaires pour la méthode de publication et sélectionnez **Valider la connexion**. Si le serveur ou la cible est disponible et que vos paramètres sont corrects, un message indique que la connexion est validée, et vous êtes prêt à publier.

    ![Valider votre connexion](../deployment/media/quickstart-publish-web-deploy.png "Valider votre connexion")

1. Sélectionnez **Paramètres** pour configurer les autres paramètres de déploiement, comme ceux qui permettent de définir s’il faut déployer une configuration Debug ou Release, puis sélectionnez **Enregistrer**. Si vous déboguez à distance, une configuration Debug est nécessaire.

1. Pour publier, sélectionnez **Publier**. La fenêtre Sortie affiche la progression du déploiement et les résultats.

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez appris à utiliser Visual Studio pour créer un profil de publication. Vous pouvez aussi configurer un profil de publication en important des paramètres de publication.

> [!div class="nextstepaction"]
> [Importer des paramètres de publication et déployer sur IIS](tutorial-import-publish-settings-iis.md)
