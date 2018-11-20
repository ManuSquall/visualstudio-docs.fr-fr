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
ms.openlocfilehash: 4f074e118d942aee2d56c30efea6854d4a0cc35e
ms.sourcegitcommit: 401be39a42ffe007593528b5bba62583ca9fcafd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2018
ms.locfileid: "50244409"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Démarrage rapide : utiliser Visual Studio pour créer votre première application web ASP.NET Core

Dans cette introduction de 5 à 10 minutes à l’utilisation de Visual Studio, vous allez créer une simple application web « Hello World » avec un modèle de projet ASP.NET et le langage de programmation C#.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="install-visual-studio"></a>Installer Visual Studio

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

### <a name="update-visual-studio"></a>Mettre à jour Visual Studio 2017

Si vous avez déjà installé Visual Studio, veillez à exécuter la version la plus récente. Pour savoir comment mettre à jour votre installation, consultez la page [Mettre à jour Visual Studio 2017 vers la version la plus récente](../install/update-visual-studio.md).

### <a name="choose-your-theme-optional"></a>Choisir votre thème (facultatif)

Ce tutoriel de démarrage rapide contient des captures d’écran qui utilisent le thème foncé. Si vous n’utilisez pas le thème foncé, mais que vous aimeriez l’utiliser, consultez la page [Personnaliser l’éditeur et l’IDE de Visual Studio](quickstart-personalize-the-ide.md) pour savoir comment faire.

## <a name="create-a-project"></a>Créer un projet

Pour commencer, vous allez créer un projet d’application web ASP.NET Core. Le type de projet s’accompagne d’entrée de jeu de tous les modèles de fichiers permettant de créer une application web.

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **Visual C#**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application web ASP.NET Core**. Ensuite, nommez votre fichier `HelloWorld` et choisissez **OK**.

   ![Créer le projet d’application web ASP.NET Core pour C#](../ide/media/csharp-aspnet-choose-template-name-file.png)

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

1. Dans la boîte de dialogue **Nouvelle application web ASP.NET Core**, sélectionnez **ASP.NET Core 2.0** ou une version ultérieure dans le menu déroulant du haut.

   > [!NOTE]
   > Si vous ne voyez pas **ASP.NET Core 2.0** ou une version ultérieure, vérifiez que vous exécutez la version la plus récente de Visual Studio. Pour savoir comment mettre à jour votre installation, consultez la page [Mettre à jour Visual Studio 2017 vers la version la plus récente](../install/update-visual-studio.md).

1. Ensuite, choisissez **Application web**, puis **OK**.

   ![Boîte de dialogue Nouvelle application web ASP.NET Core](../ide/media/quickstart-aspnet-core20.png)

Peu après, Visual Studio ouvre votre fichier projet.

## <a name="create-the-app"></a>Créer l’application

1. Dans **l’Explorateur de solutions**, développez le dossier **Pages**, puis choisissez **About.cshtml**.

   ![Choisir le fichier About.cshtml dans l’Explorateur de solutions](../ide/media/csharp-aspnet-about-page-html-file.png)

   Ce fichier correspond à la page nommée **À propos de** de l’application web.

   ![Page À propos de de l’application web](../ide/media/csharp-aspnet-about-page.png)

   L’éditeur affiche le code HTML de la zone « additional information » de la page **À propos de**.

   ![Code HTML de la zone des informations supplémentaires dans l’éditeur Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Remplacez le texte « additional information » par « **Hello World!** ».

   ![Remplacer le code HTML de la zone des informations supplémentaires dans l’éditeur Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. Dans **l’Explorateur de solutions**, développez **About.cshtml**, puis choisissez **About.cshtml.cs**. (Ce fichier correspond également à la page **À propos de** de l’application web.)

   ![Choisir le fichier About.cshtml dans l’Explorateur de solutions](../ide/media/csharp-aspnet-about-page-code-file.png)

   L’éditeur affiche le code C# comportant le texte de la zone « application description » de la page **À propos de**.

   ![Code C# de la zone de description de l’application dans l’éditeur Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Remplacez le texte du message « application description » par « **What’s my message?** ».

   ![Remplacer le texte du message par défaut de la zone de description de l’application dans l’éditeur Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

## <a name="run-the-app"></a>Exécuter l'application

1. Appuyez sur **Ctrl**+**F5** pour exécuter l’application et l’ouvrir dans un navigateur web.

   > [!NOTE]
   > Si vous obtenez le message d’erreur **Impossible de se connecter au serveur web 'IIS Express'** ou un message d’erreur qui mentionne un certificat SSL, fermez Visual Studio. Ouvrez ensuite Visual Studio à l’aide de l’option **Exécuter en tant qu’administrateur** du menu contextuel (clic droit). Ensuite, réexécutez l’application.

1. En haut de la page web, choisissez **À propos de**.

   ![Sélectionner À propos de sur la page web](../ide/media/csharp-aspnet-home-page-about.png)

1. Le texte mis à jour que vous avez ajouté à la page **À propos de** s’affiche.

   ![Afficher la page À propos de mise à jour comportant le texte ajouté](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Fermez le navigateur web.

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous en avez appris un peu plus sur C#, ASP.NET Core et l’environnement de développement intégré (IDE) Visual Studio.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus, passez au tutoriel suivant :

> [!div class="nextstepaction"]
> [Bien démarrer avec C# et ASP.NET dans Visual Studio](tutorial-csharp-aspnet-core.md)

## <a name="see-also"></a>Voir aussi

[Publier une application web sur Azure App Service avec Visual Studio](../deployment/quickstart-deploy-to-azure.md)
