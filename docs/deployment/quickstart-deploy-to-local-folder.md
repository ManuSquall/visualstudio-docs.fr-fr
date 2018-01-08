---
title: "Déployer vers un dossier local - Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords: deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
caps.latest.revision: "1"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3b97ca67c9e8d8a4cfb7d99a6c518c8e49a8c426
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2018
---
# <a name="deploy-a-web-app-or-net-core-app-to-a-local-folder-using-the-visual-studio-publish-tool"></a>Déployer une application web ou .NET Core vers un dossier local à l’aide de l’outil de publication de Visual Studio

Vous pouvez utiliser la **publier** outil à publier votre application vers un dossier local. 

Ces étapes s’appliquent aux applications Python dans Visual Studio, .NET Core, ASP.NET et ASP.NET Core. Pour Node.js, les étapes sont pris en charge, mais l’interface utilisateur est différent.

## <a name="create-a-new-project"></a>Créer un projet 

1. Dans Visual Studio, choisissez **fichier > Nouveau projet**.

1. Sous **Visual C#** ou **Visual Basic**, choisissez **.NET Core**, puis, dans le volet central, choisissez **l’application Console (.NET Core)**.

1. Tapez un nom tel que **MyLocalApp** et cliquez sur **OK**.

    Visual Studio crée le projet.

## <a name="deploy-to-a-local-folder"></a>Déployer vers un dossier local

1. Dans l’Explorateur de solutions, cliquez sur le projet et choisissez **publier**.

    ![Choisissez publier](../deployment/media/quickstart-publish.png "choisissez Publier")

1. Dans le **publier** volet, choisissez **dossier**.

    ![Choisissez le dossier](../deployment/media/quickstart-publish-folder.png "dossier")

1. Entrez un chemin d’accès ou cliquez sur **Parcourir** pour accéder à un dossier local.

1. Cliquez sur **Publier**.

    Visual Studio génère le projet et le publie dans le dossier spécifié.

    Le volet publier affiche un profil de résumé.

1. Pour configurer les paramètres de déploiement, cliquez sur **paramètres** dans le profil de résumé.

    ![Paramètres de profil](../deployment/media/quickstart-profile-settings.png "paramètres de profil") 

1. Configurer des options telles que s’il faut déployer une configuration Debug ou Release, puis cliquez sur **enregistrer**.

1. Pour publier à nouveau, cliquez sur **publier**.

Déployez les fichiers publiés de la façon qui vous convient. Par exemple, vous pouvez les empaqueter dans un fichier Zip, utilisez une commande de copie simple ou les déployer avec n’importe quel package d’installation de votre choix.

## <a name="next-steps"></a>Étapes suivantes

- [Déployer une application .NET Core avec l’outil de publication](/dotnet/core/deploying/deploy-with-vs)
- [Empaqueter une application de bureau pour Microsoft Store (pont de bureau)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)
- (.NET) [Déployer des applications et du .NET Framework](/dotnet/framework/deployment/)
