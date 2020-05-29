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
ms.openlocfilehash: 7ec5ea0b52c5d0708630a30b7d2b80be2275f3a9
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173681"
---
# <a name="publish-a-web-app-to-a-web-site-using-visual-studio"></a>Publier une application web sur un site web à l’aide de Visual Studio

Vous pouvez utiliser l’outil **Publier** pour publier des applications ASP.NET, ASP.NET Core, .NET Core et Python sur un site web à partir de Visual Studio. Pour Node.js, les étapes sont prises en charge, mais l’interface utilisateur est différente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Si vous devez publier une application de poste de travail Windows sur un partage de fichiers réseau, consultez [Déployer une application de poste de travail avec ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# ou Visual Basic). Pour C++/ CLR, consultez [Déployer une application native avec ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) ou, pour C/C++, consultez [Déployer une application native avec un projet d’installation](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="publish-to-a-web-site"></a>Publier sur un site web

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier** (ou utilisez l’élément de menu **Générer** > **Publier**).

    ![Commande publier dans le menu contextuel du projet dans Explorateur de solutions](../deployment/media/quickstart-publish.png "Choisir Publier")

1. Si vous avez déjà configuré des profils de publication, le volet **Publier** s’affiche. Cliquez sur **Créer un profil**.

1. Dans la boîte de dialogue **publier** , choisissez **serveur Web (IIS)**.

    ![Choisir la cible de publication](../deployment/media/quickstart-publish-iis.png "Choisissez IIS, FTP, etc.")

1. Choisissez **Web Deploy** comme méthode de déploiement. Web Deploy simplifie le déploiement d’applications web et de sites web sur des serveurs IIS, et doit être installé comme une application sur le serveur. Utilisez [Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx) pour l’installer.

    ![Choisir une méthode de déploiement](../deployment/media/quickstart-publish-iis-web-deploy.png "Choisissez IIS, FTP, etc.")

1. Configurez les paramètres requis pour la méthode de publication, puis sélectionnez **Terminer**. 

    ![Détails de la connexion Web Deploy](../deployment/media/quickstart-publish-iis-web-deploy-connection-details.png)

1. Pour publier, sélectionnez **publier** dans la page Résumé. La fenêtre Sortie affiche la progression du déploiement et les résultats.

## <a name="next-steps"></a>Étapes suivantes

Dans ce guide de démarrage rapide, vous avez appris à utiliser Visual Studio pour créer un profil de publication. Vous pouvez aussi configurer un profil de publication en important des paramètres de publication.

> [!div class="nextstepaction"]
> [Importer des paramètres de publication et déployer sur IIS](tutorial-import-publish-settings-iis.md)
