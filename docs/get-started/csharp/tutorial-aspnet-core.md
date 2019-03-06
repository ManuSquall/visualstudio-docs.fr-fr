---
title: 'Tutoriel : Bien démarrer avec C# et ASP.NET Core'
titleSuffix: ''
description: Découvrez comment créer une application web ASP.NET Core dans Visual Studio avec C#, pas à pas.
ms.custom: seodec18, get-started
ms.date: 10/29/2018
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 7f123646ce3b702d6e76e92009eba2ef12da7626
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55928996"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Tutoriel : Prise en main de C# et d’ASP.NET Core dans Visual Studio

Dans ce tutoriel pour le développement C# avec ASP.NET Core à l’aide de Visual Studio, vous allez créer une application web C# ASP.NET Core, y apporter des changements, explorer certaines fonctionnalités de l’environnement IDE, puis exécuter l’application.

## <a name="before-you-begin"></a>Avant de commencer

### <a name="install-visual-studio"></a>Installer Visual Studio

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) pour l’installer gratuitement.

### <a name="update-visual-studio"></a>Mettre à jour Visual Studio 2017

Si vous avez déjà installé Visual Studio, veillez à exécuter la version la plus récente. Pour savoir comment mettre à jour votre installation, consultez la page [Mettre à jour Visual Studio 2017 vers la version la plus récente](../../install/update-visual-studio.md).

### <a name="choose-your-theme-optional"></a>Choisir votre thème (facultatif)

Ce tutoriel contient des captures d’écran qui utilisent le thème foncé. Si vous n’utilisez pas le thème foncé, mais que vous aimeriez l’utiliser, consultez la page [Personnaliser l’éditeur et l’IDE de Visual Studio](../../ide/quickstart-personalize-the-ide.md) pour savoir comment faire.

## <a name="create-a-project"></a>Créer un projet

Tout d’abord, nous allons créer un projet ASP.NET Core. Le type de projet inclut tous les fichiers de modèles nécessaires à un site web parfaitement fonctionnel, avant même d’avoir ajouté quoi que ce soit !

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

3. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **Visual C#**, **Web**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application web ASP.NET Core**. Nommez ensuite le fichier *MyCoreApp*, puis choisissez **OK**.

   ![Modèle de projet d’application web ASP.NET Core dans la boîte de dialogue Nouveau projet dans l’IDE de Visual Studio](media/csharp-aspnet-choose-template-name-razor-mycoreapp-file.png)

### <a name="add-a-workload-optional"></a>Ajouter une charge de travail (facultatif)

Si vous ne voyez pas le modèle de projet **Application web ASP.NET Core**, vous pouvez l’obtenir en ajoutant la charge de travail **Développement web et ASP.NET**. Vous pouvez ajouter cette charge de travail de l’une des deux manières suivantes, en fonction des mises à jour de Visual Studio 2017 qui sont installées sur votre ordinateur.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1 : Utiliser la boîte de dialogue Nouveau projet

1. Sélectionnez le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. (Selon vos paramètres d’affichage, vous devrez peut-être faire défiler l’écran pour le voir.)

   ![Sélectionnez le lien Ouvrir Visual Studio Installer dans la boîte de dialogue Nouveau projet](../media/open-visual-studio-installer-mycoreapp.png)

1. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.

   ![Charge de travail Développement multiplateforme .Net Core dans Visual Studio Installer](../media/tutorial-aspnet-workload.png)

   (Vous devrez peut-être fermer Visual Studio pour pouvoir continuer l’installation de la nouvelle charge de travail.)

#### <a name="option-2-use-the-tools-menu-bar"></a>Option 2 : Utiliser la barre de menus Outils

1. Annulez la boîte de dialogue **Nouveau projet**. Dans la barre de menus, choisissez ensuite **Outils** > **Obtenir les outils et les fonctionnalités**.

1. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.

   (Vous devrez peut-être fermer Visual Studio pour pouvoir continuer l’installation de la nouvelle charge de travail.)

### <a name="add-a-project-template"></a>Ajouter un modèle de projet

1. Dans la boîte de dialogue **Nouvelle application web ASP.NET Core**, choisissez le modèle de projet **Application web**.

1. Vérifiez **qu’ASP.NET Core 2.1** apparaît dans le menu déroulant supérieur. Choisissez ensuite **OK**.

   ![Boîte de dialogue Nouvelle application web ASP.NET Core](media/new-project-csharp-aspnet-razor-web-app.png)

   > [!NOTE]
   > Si vous ne voyez pas **ASP.NET Core 2.0** ou ultérieur dans le menu déroulante du haut, vérifiez que vous exécutez la version la plus récente de Visual Studio. Pour savoir comment mettre à jour votre installation, consultez la page [Mettre à jour Visual Studio 2017 vers la version la plus récente](../../install/update-visual-studio.md).

### <a name="about-your-solution"></a>À propos de votre solution

Cette solution suit le modèle de conception **Razor Pages**. Il diffère du [modèle-vue-contrôleur (MVC)](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x) en ce qu’il est rationalisé de façon à intégrer le code du modèle et du contrôleur à la page Razor Pages proprement dite.

## <a name="tour-your-solution"></a>Visite guidée de votre solution

 1. Le modèle de projet crée une solution avec un seul projet ASP.NET Core nommé _MyCoreApp_. Choisissez l’onglet **Explorateur de solutions** pour afficher son contenu.

    ![Explorateur de solutions ASP.NET dans Visual Studio pour la solution Razor Pages nommée MyCoreApp](media/csharp-aspnet-razor-solution-explorer-mycoreapp.png)

 1. Développez le dossier **Pages**, puis *About.cshtml*.

     ![Fichier About.cshtml dans l’Explorateur de solutions dans Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtml.png)

 1. Affichez le fichier **About.cshtml** dans l’éditeur de code.

     ![Afficher le fichier About.cshtml dans l’éditeur de code Visual Studio](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code.png)

 1. Choisissez le fichier **About.cshtml.cs**.

     ![Choisir le fichier About.cshtml dans l’éditeur de code Visual Studio](media/csharp-aspnet-razor-solution-explorer-aboutcshtmlcs.png)

 1. Affichez le fichier **About.cshtml.cs** dans l’éditeur de code.

     ![Afficher le fichier About.cshtml dans l’éditeur de code Visual Studio](media/csharp-aspnet-razor-aboutcshtmlcs-mycoreapp-code.png)

 1. Le projet contient un dossier **wwwroot** qui représente la racine de votre site web. Développez le dossier pour voir son contenu.

     ![Dossier wwwroot dans l’Explorateur de solutions dans Visual Studio](media/csharp-aspnet-razor-solution-explorer-wwwroot.png)

    Vous pouvez placer du contenu de site statique, par exemple &mdash;des feuilles de style CSS, des images et des bibliothèques JavaScript&mdash;, directement dans les chemins souhaités.

 1. Le projet contient également des fichiers de configuration qui gèrent l’application web à l’exécution. La [configuration](/aspnet/core/fundamentals/configuration) de l’application par défaut est stockée dans *appsettings.json*. Toutefois, vous pouvez remplacer ces paramètres à l’aide de *appsettings.Development.json*. Développez le fichier **appsettings.json** pour voir le fichier **appsettings.Development.json**.

     ![Fichiers de configuration dans l’Explorateur de solutions dans Visual Studio](media/csharp-aspnet-razor-solution-explorer-appsettingsjson.png)

## <a name="run-debug-and-make-changes"></a>Exécuter, déboguer et apporter des changements

1. Choisissez le bouton **IIS Express** dans l’IDE pour générer et exécuter l’application en mode débogage. (Vous pouvez aussi appuyer sur **F5**, ou choisir **Déboguer** > **Démarrer le débogage** dans la barre de menus.)

     ![Sélectionnez le bouton IIS Express dans Visual Studio](media/csharp-aspnet-razor-iisexpress.png)

     > [!NOTE]
     > Si vous obtenez le message d’erreur **Impossible de se connecter au serveur web « IIS Express »**, fermez Visual Studio et rouvrez-le en utilisant l’option **Exécuter en tant qu’administrateur** dans le menu contextuel. Ensuite, réexécutez l’application.

1. Visual Studio lance une fenêtre de navigateur. Les pages **Home**, **About** et **Contact** apparaissent dans la barre de menus. (Si ce n’est pas le cas, sélectionnez l’élément de menu « hamburger » pour les afficher.)

    ![Sélectionner l’élément de menu « hamburger » dans la barre de menus de l’application web](media/csharp-aspnet-razor-browser-page.png)

1. Choisissez **About** dans la barre de menus.

   ![Sélectionner About dans la barre de menus de la fenêtre du navigateur de l’application](media/csharp-aspnet-razor-browser-page-about-menu.png)

   Entre autres choses, la page **About** du navigateur affiche le texte défini dans le fichier *About.cshtml*.

   ![Afficher le texte dans la page About](media/csharp-aspnet-razor-browser-page-about.png)

1. Laissez la fenêtre du navigateur ouverte et revenez dans Visual Studio.

1. Dans Visual Studio, choisissez **About.cshtml**. Ensuite, supprimez le mot _additional_ et ajoutez à la place les mots _file and directory_.

    ![Modifier le texte dans le fichier About.cshtml](media/csharp-aspnet-razor-aboutcshtml-mycoreapp-code-changed.png)

1. Choisissez **About.cshtml.cs**. Ensuite, nettoyez les directives `using` en haut du fichier à l’aide du raccourci suivant :

   Choisissez l’une des directives `using` grisées. Une ampoule [Actions rapides](../../ide/quick-actions.md) apparaît alors juste au-dessous du signe insertion ou dans la marge de gauche. Choisissez l’ampoule, puis **Supprimer les Usings inutiles**.

   ![Supprimer les instructions using inutiles dans le fichier About.cshtml.cs](media/csharp-aspnet-razor-remove-unnecessary-usings.png)

     Visual Studio supprime les directives `using` inutiles du fichier.

1. Ensuite, remplacez le corps de la méthode `OnGet()` par le code suivant :

     ```csharp
     public void OnGet()
     {
         string directory = Environment.CurrentDirectory;
     Message = String.Format("Your directory is {0}.", directory);
     }
    ```
1. Remarquez les deux soulignements ondulés qui s’affichent sous **Environment** et **String**. Ils signifient que ces types sont hors de portée.

   ![Erreurs signalées par des soulignements ondulés dans la méthode OnGet](media/csharp-aspnet-razor-add-new-on-get-method.png)

    Ouvrez la barre d’outils **Liste d’erreurs** où sont répertoriées ces mêmes erreurs. (Si la barre d’outils **Liste d’erreurs** n’est pas visible, choisissez **Afficher** > **Liste d’erreurs** dans la barre de menus supérieure.)

   ![Liste d’erreurs dans Visual Studio](media/csharp-aspnet-razor-error-list.png)

1. Nous allons résoudre ce problème. Dans l’éditeur de code, placez votre curseur sur l’une des lignes contenant l’erreur, puis choisissez l’ampoule Actions rapides dans la marge de gauche. Ensuite, dans le menu déroulant, choisissez **using System;** pour ajouter cette directive en haut de votre fichier et résoudre les erreurs.

   ![Ajouter la directive « using System; »](media/csharp-aspnet-razor-add-usings.png)

1. Appuyez sur **Ctrl**+**S** pour enregistrer vos modifications et actualiser votre application dans le navigateur web.

1. En haut du site web, choisissez **About** pour afficher vos modifications.

   ![Afficher la page About mise à jour comportant les modifications effectuées](media/csharp-aspnet-razor-browser-page-about-changed.png)

1. Fermez le navigateur web, appuyez sur **Maj**+**F5** pour arrêter le mode débogage, puis fermez Visual Studio.

## <a name="quick-answers-faq"></a>Questions fréquentes (FAQ) et réponses rapides

Voici des Questions fréquentes (FAQ) rapides pour mettre en lumière certains concepts clés.

### <a name="what-is-c"></a>Qu’est-ce que C# ?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) est un langage de programmation orienté objet et de type sécurisé conçu pour être robuste et facile à apprendre.

### <a name="what-is-aspnet-core"></a>Qu’est-ce qu’ASP.NET Core ?

ASP.NET Core est un framework open source et multiplateforme qui permet de créer des applications connectées à internet, telles que des applications et des services web. Les applications ASP.NET Core peuvent s’exécuter sur le .NET Framework ou .NET Core. Vous pouvez développer et exécuter des applications multiplateformes ASP.NET Core sur Windows, Mac et Linux. ASP.NET Core est open source dans [GitHub](https://github.com/aspnet/home).

### <a name="what-is-visual-studio"></a>Qu’est-ce que Visual Studio ?

Visual Studio est une suite de développement intégrée d’outils de productivité pour les développeurs. Il s’agit d’un programme qui sert à créer des applications et des programmes.

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce didacticiel. Nous espérons que vous en avez appris un peu plus sur C#, ASP.NET Core et l’IDE Visual Studio. Pour en savoir plus sur la création d’une application web ou d’un site web en C# et avec ASP.NET, suivez les tutoriels suivants :

> [!div class="nextstepaction"]
> [Créer une application web Razor Pages avec ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)

## <a name="see-also"></a>Voir aussi

[Publier une application web sur Azure App Service avec Visual Studio](../../deployment/quickstart-deploy-to-azure.md)
