---
title: Créer une application web ASP.NET Core dans C#
description: Découvrez comment créer une simple application web Hello World dans Visual Studio avec C# et ASP.NET Core, étape par étape.
ms.custom: mvc,seodec18
ms.date: 11/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: c87fd68a68076ab0ccab2d86f758f2217e956e26
ms.sourcegitcommit: 292ccebc601d465931fb94218a1c289c5cf77795
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73753975"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Démarrage rapide : utiliser Visual Studio pour créer votre première application web ASP.NET Core

Dans cette introduction de 5 à 10 minutes à l’utilisation de Visual Studio, vous allez créer une simple application web « Hello World » avec un modèle de projet ASP.NET et le langage de programmation C#.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="install-visual-studio"></a>Installer Visual Studio

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Choisir votre thème (facultatif)

Ce tutoriel de démarrage rapide contient des captures d’écran qui utilisent le thème foncé. Si vous n’utilisez pas le thème foncé, mais que vous aimeriez l’utiliser, consultez la page [Personnaliser l’éditeur et l’IDE de Visual Studio](quickstart-personalize-the-ide.md) pour savoir comment faire.

## <a name="create-a-project"></a>Créer un projet

Pour commencer, vous allez créer un projet d’application web ASP.NET Core. Le type de projet s’accompagne d’entrée de jeu de tous les modèles de fichiers permettant de créer une application web.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **Visual C#** , puis choisissez **.NET Core**. Dans le volet central, choisissez **Application web ASP.NET Core**. <br/><br/>Ensuite, nommez votre fichier `HelloWorld` et choisissez **OK**.

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

1. Dans la boîte de dialogue **Nouvelle application web ASP.NET Core**, sélectionnez **ASP.NET Core 2.1** dans le menu déroulant supérieur. Ensuite, choisissez **Application web**, puis **OK**.

   ![Boîte de dialogue Nouvelle application web ASP.NET Core](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Si vous ne voyez pas **ASP.NET Core 2.1**, vérifiez que vous exécutez la version la plus récente de Visual Studio. Pour plus d’informations sur la mise à jour votre installation, consultez la page [Mettre à jour Visual Studio vers la version la plus récente](../install/update-visual-studio.md).

Peu après, Visual Studio ouvre votre fichier projet.

::: moniker-end

::: moniker range="vs-2019"

1. Ouvrez Visual Studio.

1. Dans la fenêtre de démarrage, choisissez **Créer un projet**.

   ![Afficher la fenêtre « Créer un projet »](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Dans la fenêtre **Créer un projet**, entrez ou tapez *ASP.NET* dans la zone de recherche. Ensuite, choisissez **C#** Dans la liste des langages, puis choisissez **Windows** dans la liste des plateformes.

   Après avoir appliqué les filtres de langage et de plateforme, choisissez le modèle **Application web ASP.NET Core**, puis choisissez **Suivant**.

   ![Choisir le modèle C# pour l’application web ASP.NET Core](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > Si vous ne voyez pas le modèle **Application web ASP.NET Core**, vous pouvez l’installer à partir de la fenêtre **Créer un projet**. Dans le **Vous ne trouvez pas ce que vous cherchez ?** , choisissez le lien **Installer plus d’outils et de fonctionnalités**.
   >
   > ![Le lien « Installer plus d’outils et de fonctionnalités » du message « Vous ne trouvez pas ce que vous cherchez ? » dans la fenêtre « Créer un projet »](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ensuite, dans Visual Studio Installer, choisissez la charge de travail **Développement web et ASP.NET**.
   >
   > ![Charge de travail Application web ASP.NET Core dans Visual Studio Installer](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Après cela, choisissez le bouton **Modifier** dans Visual Studio Installer. Vous pouvez être invité à enregistrer votre travail ; le cas échéant, faites-le. Ensuite, choisissez **Continuer** pour installer la charge de travail. Ensuite, revenez à l’étape 2 de cette procédure « [Créer un projet](#create-a-project) ».

1. Dans la fenêtre **Configurer votre nouveau projet**, tapez ou entrez *HelloWorld* dans la zone **Nom du projet**. Choisissez ensuite **Créer**.

   ![Dans la fenêtre « Configurer votre nouveau projet », nommez votre projet « HelloWorld »](../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png)

1. Dans la fenêtre **créer une nouvelle ASP.net Core application Web** , vérifiez que **ASP.net Core 3,0** s’affiche dans le menu déroulant supérieur. Ensuite, choisissez **Application web**, qui inclut des exemples Razor Pages. Ensuite, choisissez **Créer**.

   ![La fenêtre « Créez une application web ASP.NET Core »](../get-started/csharp/media/vs-2019/csharp-create-aspnet-razor-pages-app.png)

   Visual Studio ouvre votre nouveau projet.

::: moniker-end

## <a name="create-and-run-the-app"></a>Créer et exécuter l’application

::: moniker range="vs-2017"

1. Dans **l’Explorateur de solutions**, développez le dossier **Pages**, puis choisissez **About.cshtml**.

   ![Choisir le fichier About.cshtml dans l’Explorateur de solutions](../ide/media/csharp-aspnet-about-page-html-file.png)

   Ce fichier correspond à la page nommée **About** de l’application web, qui exécute un navigateur web.

   ![Page À propos de de l’application web](../ide/media/csharp-aspnet-about-page.png)

   L’éditeur affiche le code HTML de la zone « additional information » de la page **À propos de**.

   ![Code HTML de la zone des informations supplémentaires dans l’éditeur Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Remplacez le texte « additional information » par « **Hello World!** ».

   ![Remplacer le code HTML de la zone des informations supplémentaires dans l’éditeur Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. Dans **l’Explorateur de solutions**, développez **About.cshtml**, puis choisissez **About.cshtml.cs**. (Ce fichier correspond également à la page **À propos de** d’un navigateur web.)

   ![Choisir le fichier About.cshtml dans l’Explorateur de solutions](../ide/media/csharp-aspnet-about-page-code-file.png)

   L’éditeur affiche le code C# comportant le texte de la zone « application description » de la page **À propos de**.

   ![Code C# de la zone de description de l’application dans l’éditeur Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Remplacez le texte du message « application description » par « **What’s my message?** ».

   ![Remplacer le texte du message par défaut de la zone de description de l’application dans l’éditeur Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Choisissez **IIS Express** ou appuyez sur **Ctrl**+**F5** pour exécuter l’application et l’ouvrir dans un navigateur web.

   ![Sélectionnez le bouton IIS Express dans Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Si vous obtenez le message d’erreur **Impossible de se connecter au serveur web 'IIS Express'** ou un message d’erreur qui mentionne un certificat SSL, fermez Visual Studio. Ensuite, ouvrez Visual Studio en utilisant l’option **Exécuter en tant qu’administrateur** du menu contextuel (clic droit). Ensuite, réexécutez l’application.

1. Dans le navigateur web, vérifiez que la page **About** comporte votre texte mis à jour.

   ![Afficher la page About mise à jour comportant les modifications effectuées](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Fermez le navigateur web.

### <a name="review-your-work"></a>Passer en revue votre travail

Regardez l’animation suivante pour vérifier le travail que vous avez effectué dans la section précédente.

  ![Regarder le fichier .gif animé qui montre comment créer et exécuter une application web C# ASP.NET Core simple dans Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous en avez appris un peu plus sur C#, ASP.NET Core et l’environnement de développement intégré (IDE) Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. Dans le **Explorateur de solutions**, développez le dossier **pages** , puis choisissez **index. cshtml**.

   ![Sélectionnez le fichier index. cshtml dans la Explorateur de solutions](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Ce fichier correspond à une page nommée **démarrage** dans l’application Web, qui s’exécute dans un navigateur Web.

   ![Page À propos de de l’application web](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   Dans l’éditeur, vous verrez le code HTML pour le texte qui s’affiche sur la page d' **hébergement** .

   ![Code HTML du fichier index. cshtml pour la page d’hébergement dans l’éditeur Visual Studio](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. Modifiez le texte « Bienvenue » pour lire «**Hello World !** ».

   ![Dans l’éditeur Visual Studio, modifiez le code HTML par défaut qui indique Hello World à la place.](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Choisissez **IIS Express** ou appuyez sur **Ctrl**+**F5** pour exécuter l’application et l’ouvrir dans un navigateur web.

   ![Sélectionnez le bouton IIS Express dans Visual Studio](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > Si vous obtenez le message d’erreur **Impossible de se connecter au serveur web 'IIS Express'** ou un message d’erreur qui mentionne un certificat SSL, fermez Visual Studio. Ensuite, ouvrez Visual Studio en utilisant l’option **Exécuter en tant qu’administrateur** du menu contextuel (clic droit). Ensuite, réexécutez l’application.

1. Dans le navigateur Web, vérifiez que la page d' **hébergement** comprend votre texte mis à jour.

   ![Afficher la page d’hébergement mise à jour qui comprend les modifications apportées](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Fermez le navigateur web.

::: moniker-end

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus, passez au tutoriel suivant :

> [!div class="nextstepaction"]
> [Bien démarrer avec C# et ASP.NET dans Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Voir aussi

[Publier une application web sur Azure App Service avec Visual Studio](../deployment/quickstart-deploy-to-azure.md)
