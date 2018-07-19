---
title: Déployer sur un dossier local
ms.custom: ''
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 517698aa2e042d74138579dae3633930b338cd61
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "38781911"
---
# <a name="deploy-an-app-to-a-local-folder-using-visual-studio"></a>Déployer une application dans un dossier local à l’aide de Visual Studio

Vous pouvez utiliser la **publier** outil pour publier des applications ASP.NET, ASP.NET Core, .NET Core et Python dans un dossier local à partir de Visual Studio. Pour Node.js, les étapes sont pris en charge, mais l’interface utilisateur est différente.

[!INCLUDE [quickstart-prereqs](includes/quickstart-prereqs.md)]

## <a name="deploy-to-a-local-folder"></a>Déployer sur un dossier local

1. Dans l’Explorateur de solutions, cliquez sur le projet et choisissez **publier** (ou utilisez le **Build** > **publier** élément de menu).

    ![La commande Publier sur le menu contextuel du projet dans l’Explorateur de solutions](../deployment/media/quickstart-publish.png "choisissez Publier")

1. Si vous avez déjà configuré des profils de publication, le **publier** volet s’affiche. Sélectionnez **créer nouveau profil**.

1. Dans le **choisir une cible de publication** boîte de dialogue, sélectionnez **dossier**.

    ![Choisir un dossier local comme un cibles de publication](../deployment/media/quickstart-publish-folder.png "choisir un dossier")

1. Entrez un chemin d’accès ou sélectionnez **Parcourir** pour spécifier un dossier local.

1. Sélectionnez **Publier**. Visual Studio génère le projet et le publie dans le dossier spécifié. Les propriétés du projet **publier** volet apparaît, affichant un profil de résumé.

    ![Publier le volet des propriétés affichant un profil de résumé](../deployment/media/quickstart-publish-folder-summary.png)

1. Pour configurer les paramètres de déploiement, sélectionnez **configurer** dans le profil de résumé et sélectionnez le **paramètres** onglet.

    ![Paramètres de profil](../deployment/media/quickstart-profile-settings.png "paramètres de profil")

1. Configurer des options comme s’il faut déployer une configuration Debug ou Release, puis sélectionnez **enregistrer**.

1. Pour publier à nouveau, sélectionnez **publier**.

Déployez les fichiers publiés de la façon qui vous convient. Par exemple, vous pouvez les empaqueter dans un *.zip* de fichiers, utilisez une commande de copie simple ou les déployer avec n’importe quel package d’installation de votre choix.

## <a name="next-steps"></a>Étapes suivantes

- [Déployer une application .NET Core avec l’outil de publication](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Empaqueter une application de bureau pour Microsoft Store (pont de bureau)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- (.NET) [Déployer des applications et du .NET Framework](/dotnet/framework/deployment/)
