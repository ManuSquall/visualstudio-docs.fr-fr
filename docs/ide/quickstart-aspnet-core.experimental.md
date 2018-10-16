---
title: Utiliser Visual Studio pour créer une application web ASP.NET Core dans C#
description: Découvrez comment créer une simple application web Hello World dans Visual Studio avec C# et ASP.NET Core, étape par étape.
ms.custom: mvc
ms.date: 09/23/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 53bed90ea686897c2a668ddbc64c60a95c8edfe8
ms.sourcegitcommit: 25fc9605ba673afb51a24ce587cf4304b06aa577
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47028934"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Démarrage rapide : utiliser Visual Studio pour créer votre première application web ASP.NET Core

Dans cette introduction de 5 à 10 minutes à l’utilisation de Visual Studio, vous allez créer une simple application web « Hello World » avec un modèle de projet ASP.NET et le langage de programmation C#.

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

## <a name="create-a-project"></a>Créer un projet

Vous allez d’abord créer un projet d’application web ASP.NET Core. Voici comment procéder.

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **Visual C#**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application web ASP.NET Core**. Ensuite, nommez votre fichier `HelloWorld` et choisissez **OK**.

1. Dans la boîte de dialogue **Nouvelle application web ASP.NET Core**, vérifiez que **ASP.NET Core 2.0** apparaît dans le menu déroulant supérieur. Ensuite, choisissez **Application web** et sélectionnez **OK**.

   ![Afficher le fichier .gif animé qui montre comment créer un projet C# ASP.NET Core dans Visual Studio](../ide/media/csharp-aspnet-animated-create-project.gif)

   Peu après, Visual Studio ouvre votre fichier projet.

   > [!NOTE]
   > Si vous ne voyez pas la catégorie du modèle de projet **.NET Core**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche.
   >
   > ![Ouvrir Visual Studio Installer dans la boîte de dialogue Nouveau projet](../ide/media/open-visual-studio-installer.png)
   >
   > Visual Studio Installer est lancé. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.
   >
   > ![Charge de travail ASP.NET dans Visual Studio Installer](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Vous devrez peut-être fermer Visual Studio pour pouvoir continuer l’installation de la nouvelle charge de travail.)

## <a name="create-and-run-the-app"></a>Créer et exécuter l’application

Ensuite, vous allez créer et exécuter votre application web « Hello World ». Voici comment procéder.

1. Dans **l’Explorateur de solutions** de Visual Studio, développez le dossier **Pages**. Ensuite, choisissez **About.cshtml**.

   ![Choisir le fichier About.cshtml dans l’Explorateur de solutions](../ide/media/csharp-aspnet-about-page-html-file.png)

   Ce fichier correspond à la page nommée **About** de l’application web, qui exécute un navigateur web.

   ![Page À propos de de l’application web](../ide/media/csharp-aspnet-about-page.png)

1. Dans l’éditeur de code Visual Studio, remplacez le texte « additional information » par « **Hello World!** ».

1. Dans **l’Explorateur de solutions**, développez **About.cshtml**, puis choisissez **About.cshtml.cs**.

1. Remplacez le texte du message « application description » par « **What’s my message?** ».

1. Choisissez **IIS Express** ou appuyez sur **Ctrl**+**F5** pour exécuter l’application et l’ouvrir dans un navigateur web.

   ![Afficher le fichier .gif animé qui montre comment créer et exécuter une application web C# ASP.NET Core dans Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

   > [!NOTE]
   > Si un message d’erreur indique **Impossible de se connecter au serveur web « IIS Express »**, fermez Visual Studio et rouvrez-le en utilisant l’option **Exécuter en tant qu’administrateur** dans le menu contextuel. Ensuite, réexécutez l’application.

1. Dans le navigateur web, vérifiez que la page **About** comporte votre texte mis à jour.

1. Fermez le navigateur web.

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous en avez appris un peu plus sur C#, ASP.NET Core et l’environnement de développement intégré (IDE) Visual Studio.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus, passez au tutoriel suivant :

> [!div class="nextstepaction"]
> [Bien démarrer avec C# et ASP.NET dans Visual Studio](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>Voir aussi

[Publier une application web sur Azure App Service avec Visual Studio](..//deployment/quickstart-deploy-to-azure.md)
