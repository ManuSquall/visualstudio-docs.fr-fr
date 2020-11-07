---
title: Déployer sur un dossier local
description: Découvrez comment utiliser l’outil de publication pour publier des applications ASP.NET, ASP.NET Core, .NET Core et Python dans un dossier à partir de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/29/2019
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f392cc2dcb474487a37076229c0b10f7359b9251
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349566"
---
# <a name="deploy-an-app-to-a-folder-using-visual-studio"></a>Déployer une application dans un dossier à l’aide de Visual Studio

Vous pouvez utiliser l’outil de **publication** pour publier des applications ASP.NET, ASP.net Core, .net Core et Python dans un dossier à partir de Visual Studio. Pour Node.js, les étapes sont prises en charge, mais l’interface utilisateur est différente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Si vous devez publier une application de bureau Windows dans un dossier, consultez [déployer une application de bureau à l’aide de ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# ou Visual Basic). Pour C++/ CLR, consultez [Déployer une application native avec ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) ou, pour C/C++, consultez [Déployer une application native avec un projet d’installation](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="deploy-to-a-local-folder"></a>Déployer sur un dossier local

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier** (ou utilisez l’élément de menu **Générer** > **Publier** ).

    ![Commande publier dans le menu contextuel du projet dans Explorateur de solutions](../deployment/media/quickstart-publish.png "Choisir Publier")

1. Si vous avez déjà configuré des profils de publication, la fenêtre **publier** s’affiche. Sélectionnez **Nouveau**.

1. Dans la fenêtre **publier** , sélectionnez **dossier**.

    ![Choisir un dossier en tant que cible de publication](../deployment/media/quickstart-publish-folder-new.png "Choisir un dossier")

1. Entrez un chemin d’accès ou sélectionnez **Parcourir** pour spécifier un dossier.

    ![Spécifier le chemin d’accès au dossier](../deployment/media/quickstart-publish-folder-path.png "Choisir un dossier")

1. Sélectionnez **Publier**. Visual Studio génère le projet et le publie dans le dossier spécifié. Le volet **Publier** des propriétés de projet apparaît, affichant un récapitulatif du profil.

    ![Volet de propriétés Publier affichant un récapitulatif du profil](../deployment/media/quickstart-publish-folder-summary.png)

1. Pour configurer les paramètres de déploiement, sélectionnez **modifier** dans le résumé du profil de publication et sélectionnez l’onglet **paramètres** .

   Les paramètres que vous voyez dépendent du type de votre application. L’illustration suivante montre des exemples de paramètres pour une application ASP.NET Core.

    ![Paramètres de profil](../deployment/media/quickstart-profile-settings.png "Paramètres de profil")

    Pour obtenir une aide supplémentaire pour choisir des paramètres dans .NET, consultez les rubriques suivantes :

    - [Déploiement dépendant du Framework et déploiement autonome](/dotnet/core/deploying/)
    - [Identificateurs du runtime cible (RID portable, et al)](/dotnet/core/rid-catalog)
    - [Configurations Debug et Release](../ide/understanding-build-configurations.md)

1. Configurez les options qui permettent de définir s’il faut déployer une configuration Debug ou Release, puis sélectionnez **Enregistrer**.

1. Pour republier, sélectionnez **Publier**.

Déployez les fichiers publiés de la façon qui vous convient. Par exemple, vous pouvez les empaqueter dans un fichier *.zip* , utiliser une simple commande de copie ou les déployer avec le package d’installation de votre choix.

## <a name="next-steps"></a>Étapes suivantes

Pour les applications .NET :

- [Déployer une application .NET Core avec l’outil de publication](/dotnet/core/deploying/deploy-with-vs)
- [Publication d’applications .NET Core (déploiements dépendants du Framework et déploiements autonomes)](/dotnet/core/deploying/)
- [Déployer les applications .NET Framework et](/dotnet/framework/deployment/)
