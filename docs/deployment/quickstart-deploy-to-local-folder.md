---
title: Déployer sur un dossier local
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
ms.openlocfilehash: 862310c8c763ce366798bfacd4f4759d606bb33c
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128209"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Déployer une application dans un dossier local à l’aide de Visual Studio

Vous pouvez utiliser l’outil **Publier** pour publier des applications ASP.NET, ASP.NET Core, .NET Core et Python dans un dossier local à partir de Visual Studio. Pour Node.js, les étapes sont prises en charge, mais l’interface utilisateur est différente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

> [!NOTE]
> Si vous devez publier une application de poste de travail Windows sur un dossier local, consultez [Déployer une application de poste de travail avec ClickOnce](how-to-publish-a-clickonce-application-using-the-publish-wizard.md) (C# ou Visual Basic). Pour C++/CLI, consultez [déployer une application native à l’aide de ClickOnce](/cpp/windows/clickonce-deployment-for-visual-cpp-applications) ou,C++pour C/, consultez [déployer une application native à l’aide d’un projet d’installation](/cpp/windows/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project).

## <a name="deploy-to-a-local-folder"></a>Déployer sur un dossier local

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier** (ou utilisez l’élément de menu **Générer** > **Publier**).

    ![Commande Publier du menu contextuel du projet dans l’Explorateur de solutions](../deployment/media/quickstart-publish.png "Choisissez Publier")

1. Si vous avez déjà configuré des profils de publication, le volet **Publier** s’affiche. Cliquez sur **Créer un profil**.

1. Dans la boîte de dialogue **Choisir une cible de publication**, choisissez **Dossier**.

    ![Choisir un dossier local comme cible de publication](../deployment/media/quickstart-publish-folder.png "Choisir un dossier")

1. Entrez un chemin ou sélectionnez **Parcourir** pour spécifier un dossier local.

1. Sélectionnez **Publier**. Visual Studio génère le projet et le publie dans le dossier spécifié. Le volet **Publier** des propriétés de projet apparaît, affichant un récapitulatif du profil.

    ![Volet de propriétés Publier affichant un récapitulatif du profil](../deployment/media/quickstart-publish-folder-summary.png)

1. Pour configurer les paramètres de déploiement, sélectionnez **Configurer** dans le récapitulatif du profil, puis l’onglet **Paramètres**.

    ![Paramètres de profil](../deployment/media/quickstart-profile-settings.png "Paramètres de profil")

1. Configurez les options qui permettent de définir s’il faut déployer une configuration Debug ou Release, puis sélectionnez **Enregistrer**.

1. Pour republier, sélectionnez **Publier**.

Déployez les fichiers publiés de la façon qui vous convient. Par exemple, vous pouvez les empaqueter dans un fichier *.zip*, utiliser une simple commande de copie ou les déployer avec le package d’installation de votre choix.

## <a name="next-steps"></a>Étapes suivantes

- [Déployer une application .NET Core avec l’outil de publication](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Empaqueter une application de bureau pour Microsoft Store (pont de bureau)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Déployer le .NET Framework et des applications](/dotnet/framework/deployment/)
