---
title: "Déployer vers un dossier local - Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: quickstart
helpviewer_keywords:
- deployment, local folder
ms.assetid: adb461c4-812a-4b8c-b2ab-96002379f6a9
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4e575a6d885b079c1c5afd0af6cbdadcd1d38d96
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="deploy-a-web-app-or-net-core-app-to-a-local-folder-using-the-visual-studio-publish-tool"></a>Déployer une application web ou .NET Core vers un dossier local à l’aide de l’outil de publication de Visual Studio

Vous pouvez utiliser l'outil de **publication** pour publier votre application vers un dossier local. 

Ces étapes s’appliquent aux applications ASP.NET, ASP.NET Core, .NET Core, et Python dans Visual Studio. Pour Node.js, les étapes sont prises en charge, mais l’interface utilisateur est différente.

## <a name="create-a-new-project"></a>Créer un nouveau projet 

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau > Projet**.

1. Sous **Visual C#** ou **Visual Basic**, choisissez **.NET Core**, puis, dans le volet central, choisissez **Application Console (.NET Core)**.

1. Tapez un nom tel que **MonApplicationLocale** et cliquez sur **OK**.

    Visual Studio crée le projet.

## <a name="deploy-to-a-local-folder"></a>Déployer vers un dossier local

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet et choisissez **Publier**.

    ![Choisissez publier](../deployment/media/quickstart-publish.png "choisissez Publier")

1. Dans le volet **publier**, choisissez **dossier**.

    ![Choisissez le dossier](../deployment/media/quickstart-publish-folder.png "dossier")

1. Entrez un chemin d’accès ou cliquez sur **Parcourir** pour accéder à un dossier local.

1. Cliquez sur **Publier**.

    Visual Studio génère le projet et le publie dans le dossier spécifié.

    Le volet publier affiche un résumé de profil.

1. Pour configurer les paramètres de déploiement, cliquez sur **paramètres** dans le résumé de profil.

    ![Paramètres de profil](../deployment/media/quickstart-profile-settings.png "paramètres de profil") 

1. Configurez des options telles que la configuration de déploiement en Debug ou en Release, puis cliquez sur **enregistrer**.

1. Pour publier à nouveau, cliquez sur **publier**.

Déployez les fichiers publiés de la façon qui vous convient. Par exemple, vous pouvez les empaqueter dans un fichier Zip, utilisez une simple commande `copy` ou les déployer avec n’importe quel package d’installation de votre choix.

## <a name="next-steps"></a>Étapes suivantes

- [Déployer une application .NET Core avec l’outil de publication](/dotnet/core/deploying/deploy-with-vs)
- [Empaqueter une application de bureau pour Microsoft Store (pont de bureau)](/windows/uwp/porting/desktop-to-uwp-packaging-dot-net)
- (.NET) [Déployer des applications et du .NET Framework](/dotnet/framework/deployment/)
