---
title: Utiliser Visual Studio pour créer une application web ASP.NET Core dans C#
description: Découvrez comment créer une simple application web Hello World dans Visual Studio avec C# et ASP.NET Core, étape par étape.
ms.custom: mvc
ms.date: 10/29/2018
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
ms.openlocfilehash: e85650f6671684f2d0ed313603f1af88e608e1d9
ms.sourcegitcommit: 401be39a42ffe007593528b5bba62583ca9fcafd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50244422"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Démarrage rapide : utiliser Visual Studio pour créer votre première application web ASP.NET Core

Dans cette introduction de 5 à 10 minutes à l’utilisation de Visual Studio, vous allez créer une simple application web « Hello World » avec un modèle de projet ASP.NET et le langage de programmation C#.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="install-visual-studio"></a>Installer Visual Studio

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

### <a name="update-visual-studio"></a>Mettre à jour Visual Studio 2017

Si vous avez déjà installé Visual Studio, veillez à exécuter la version la plus récente. Pour savoir comment mettre à jour votre installation, consultez la page [Mettre à jour Visual Studio 2017 vers la version la plus récente](../install/update-visual-studio.md).

### <a name="choose-your-theme-optional"></a>Choisir votre thème (facultatif)

Ce tutoriel de démarrage rapide contient des captures d’écran qui utilisent le thème foncé. Si vous n’utilisez pas le thème foncé mais que vous aimeriez l’utiliser, consultez la page [Personnaliser l’éditeur et l’IDE de Visual Studio](quickstart-personalize-the-ide.md) pour savoir comment faire.

## <a name="create-a-project"></a>Créer un projet

Pour commencer, vous allez créer un projet d’application web ASP.NET Core. Voici comment procéder.

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **Visual C#**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application web ASP.NET Core**. Ensuite, nommez votre fichier `HelloWorld` et choisissez **OK**.

1. Dans la boîte de dialogue **Nouvelle application web ASP.NET Core**, sélectionnez **ASP.NET Core 2.0** ou une version ultérieure dans le menu déroulant du haut, puis sélectionnez**Application web**.

   > [!NOTE]
   > Si vous ne voyez pas **ASP.NET Core 2.0** ou ultérieur dans le menu déroulante du haut, vérifiez que vous exécutez la version la plus récente de Visual Studio. Pour savoir comment mettre à jour votre installation, consultez la page [Mettre à jour Visual Studio 2017 vers la version la plus récente](../install/update-visual-studio.md).

   ![Afficher le fichier .gif animé qui montre comment créer un projet C# ASP.NET Core dans Visual Studio](../ide/media/csharp-aspnet-animated-create-project.gif)

   Peu après, Visual Studio ouvre votre fichier projet.

   > [!NOTE]
   > Si vous ne voyez pas la catégorie du modèle de projet **.NET Core**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche. (Selon vos paramètres d’affichage, vous devrez peut-être faire défiler l’écran pour le voir.)
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
   > Si vous obtenez le message d’erreur **Impossible de se connecter au serveur web 'IIS Express'** ou un message d’erreur qui mentionne un certificat SSL, fermez Visual Studio. Ouvrez ensuite Visual Studio à l’aide de l’option **Exécuter en tant qu’administrateur** du menu contextuel (clic droit). Ensuite, réexécutez l’application.

1. Dans le navigateur web, vérifiez que la page **About** comporte votre texte mis à jour.

1. Fermez le navigateur web.

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous en avez appris un peu plus sur C#, ASP.NET Core et l’environnement de développement intégré (IDE) Visual Studio.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus, passez au tutoriel suivant :

> [!div class="nextstepaction"]
> [Bien démarrer avec C# et ASP.NET dans Visual Studio](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>Voir aussi

[Publier une application web sur Azure App Service avec Visual Studio](..//deployment/quickstart-deploy-to-azure.md)
