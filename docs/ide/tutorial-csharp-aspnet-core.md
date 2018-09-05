---
title: Prise en main de C# et d’ASP.NET Core dans Visual Studio
description: Découvrez comment créer une application web ASP.NET Core dans Visual Studio avec C#, pas à pas.
ms.custom: ''
ms.date: 08/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: fb1532a76d9bc530146ba5a0f563bcaa9389226c
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2018
ms.locfileid: "42626615"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Tutoriel : Bien démarrer avec C# et ASP.NET Core dans Visual Studio

Dans ce tutoriel pour le développement C# avec ASP.NET Core à l’aide de Visual Studio, vous allez créer une application web C# ASP.NET Core, y apporter des changements, explorer certaines fonctionnalités de l’IDE et exécuter l’application.

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

## <a name="create-a-project"></a>Créer un projet

Tout d’abord, nous allons créer un projet ASP.NET Core. Le type de projet inclut tous les fichiers de modèles dont vous avez besoin pour un site web, avant même d’avoir ajouté quoi que ce soit !

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**. 

3. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **Visual C#**, **Web**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application web ASP.NET Core**. Nommez ensuite le fichier *MyCoreApp*, puis choisissez **OK**.

   ![Modèle de projet d’application web ASP.NET Core dans la boîte de dialogue Nouveau projet dans l’IDE de Visual Studio](../ide/media/csharp-aspnet-choose-template-name-mycoreapp-mvc.png)

### <a name="add-a-workload-optional"></a>Ajouter une charge de travail (facultatif)

Si vous ne voyez pas le modèle de projet **Application web ASP.NET Core**, vous pouvez l’obtenir en ajoutant la charge de travail **Développement web et ASP.NET**. Vous pouvez ajouter cette charge de travail de l’une des deux manières suivantes, en fonction des mises à jour de Visual Studio 2017 qui sont installées sur votre ordinateur.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1 : Utiliser la boîte de dialogue Nouveau projet

1. Sélectionnez le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**.

   ![Sélectionnez le lien Ouvrir Visual Studio Installer dans la boîte de dialogue Nouveau projet](../ide/media/vs-open-visual-studio-installer-generic.png)

1. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.

   ![Charge de travail Développement multiplateforme .Net Core dans Visual Studio Installer](../ide/media/quickstart-aspnet-workload.png)

   (Vous devrez peut-être fermer Visual Studio pour pouvoir continuer l’installation de la nouvelle charge de travail.)

#### <a name="option-2-use-the-tools-menu-bar"></a>Option 2 : Utiliser la barre de menus Outils

1. Annulez la boîte de dialogue **Nouveau projet**. Dans la barre de menus, choisissez ensuite **Outils** > **Obtenir les outils et les fonctionnalités**.

1. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement web et ASP.NET**, puis **Modifier**.

   (Vous devrez peut-être fermer Visual Studio pour pouvoir continuer l’installation de la nouvelle charge de travail.)

### <a name="add-a-project-template"></a>Ajouter un modèle de projet

1. Dans la boîte de dialogue **Nouvelle application web ASP.NET Core**, choisissez le modèle de projet **Application web (Model-View-Controller)**.

1. Vérifiez qu’**ASP.NET Core 2.0** apparaît dans le menu déroulant supérieur. Choisissez ensuite **OK**.

   ![Boîte de dialogue Nouvelle application web ASP.NET Core](../ide/media/new-project-csharp-aspnet-web-app-mvc.png)

### <a name="about-your-solution"></a>À propos de votre solution

Cette solution suit le modèle d’architecture MVC (Model-View-Controller), qui sépare une application en trois composants principaux :

* Les **Modèles** incluent des classes qui représentent les données de l’application. Les classes du modèle utilisent une logique de validation pour appliquer des règles d’entreprise à ces données. En règle générale, les objets du modèle récupèrent et stockent l’état du modèle dans une base de données.
* Les **vues** sont les composants qui affichent l’interface utilisateur de l’application. En règle générale, cette interface utilisateur affiche les données du modèle.
* Les **contrôleurs** incluent les classes qui gèrent les demandes du navigateur. Ils récupèrent les données du modèle et appellent les modèles de vue qui retournent une réponse. Dans une application MVC, la vue affiche seulement les informations ; le contrôleur gère et répond aux entrées et aux interactions de l’utilisateur.

Le modèle MVC vous permet de créer des applications qui sont plus faciles à tester et à mettre à jour que les applications monolithiques traditionnelles.

## <a name="tour-your-solution"></a>Visite guidée de votre solution

 1. Le modèle de projet crée une solution avec un seul projet ASP.NET Core nommé **MyCoreApp**. Développez le nœud de projet pour exposer son contenu.

    ![Explorateur de solutions ASP.NET dans Visual Studio](../ide/media/csharp-aspnet-solution-explorer-mycoreapp-mvc.png)

 1. Ouvrez le fichier *HomeController.cs* dans le dossier **Controllers**.

     ![Fichier HomeController.cs dans l’Explorateur de solutions dans Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

 1. Affichez le fichier *HomeController.cs*.

     ![HomeController.cs dans la fenêtre de code de Visual Studio](../ide/media/csharp-aspnet-home-controller-code.png)

 1. Le projet a également un dossier **Vues** qui contient des sous-dossiers mappés à chaque contrôleur. Par exemple, le fichier CSHTML de vue (une extension du langage HTML) pour le chemin */Home/About* se trouverait à l’emplacement *Views/Home/About.cshtml*. Ouvrez ce fichier.

     ![Fichier About.cshtml dans l’Explorateur de solutions dans Visual Studio](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

    Ce fichier CSHTML utilise la syntaxe Razor pour afficher le code HTML d’après une combinaison de balises standard et de code C# inline.

     ![About.cshtml dans la fenêtre de code de Visual Studio](../ide/media/csharp-aspnet-about-cshtml-code.png)

    >[!NOTE]
    > Pour plus d’informations sur Razor, consultez la page [Bien démarrer avec C# et ASP.NET à l’aide de la syntaxe Razor](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

 1. Le projet contient également un dossier **wwwroot** qui représente la racine de votre site web. Développez le dossier pour voir son contenu.

     ![Dossier wwwroot dans l’Explorateur de solutions dans Visual Studio](../ide/media/csharp-aspnet-solution-wwwroot.png)

    Vous pouvez placer du contenu de site statique, par exemple &mdash;des feuilles de style CSS, des images et des bibliothèques JavaScript&mdash;, directement dans les chemins souhaités.

 1. Plusieurs fichiers config gèrent le projet, ses packages et l’application au moment de l’exécution. Par exemple, la [configuration](/aspnet/core/fundamentals/configuration) d’application par défaut est stockée dans *appsettings.json*. Toutefois, vous pouvez remplacer ces paramètres à l’aide de *appsettings.Development.json*. Développez le fichier **appsettings.json** pour voir le fichier **appsettings.Development.json**.

     ![Fichiers de configuration dans l’Explorateur de solutions dans Visual Studio](../ide/media/csharp-aspnet-solution-explorer-config-files.png)

## <a name="run-debug-and-make-changes"></a>Exécuter, déboguer et apporter des changements

1. Choisissez le bouton **IIS Express** dans l’IDE pour générer et exécuter l’application en mode débogage. (Vous pouvez aussi appuyer sur **F5**, ou choisir **Déboguer > Démarrer le débogage** dans la barre de menus.)

     ![Sélectionnez le bouton IIS Express dans Visual Studio](../ide/media/csharp-aspnet-iis-express-button.png)

     > [!NOTE]
     > Si vous obtenez le message d’erreur **Impossible de se connecter au serveur web « IIS Express »**, fermez Visual Studio et rouvrez-le en utilisant l’option **Exécuter en tant qu’administrateur** dans le menu contextuel. Ensuite, réexécutez l’application.

1. Visual Studio lance une fenêtre de navigateur. Sélectionnez **About**.

   ![Sélectionnez About dans la fenêtre du navigateur pour votre application](../ide/media/csharp-aspnet-browser-page.png)

   Entre autres choses, la page **About** dans le navigateur affiche le texte qui est défini dans le fichier *HomeController.cs*.

   ![Afficher le texte dans la page About](../ide/media/csharp-aspnet-browser-page-about.png)

1. Laissez la fenêtre du navigateur ouverte et revenez dans Visual Studio. Ouvrez *Controllers/HomeController.cs* s’il n’est pas déjà ouvert.

   ![Ouvrez le fichier HomeController.cs à partir de l’Explorateur de solutions dans Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

1. Définissez un point d’arrêt sur la première ligne de la méthode **About**. Pour ce faire, cliquez dans la marge ou placez le curseur sur la ligne et appuyez sur **F9**.

   Cette ligne définit certaines données dans la collection **ViewData** qui sont affichées dans la page CSHTML *Views/Home/About.cshtml*.

   ![Définissez un point d’arrêt sur la première ligne de la méthode About dans About.cshtml.  ](../ide/media/csharp-aspnet-home-controller-code-set-breakpoint.png)

1. Revenez dans le navigateur et actualisez la page **About**. Cette opération déclenche le point d’arrêt dans Visual Studio.

1. Dans Visual Studio, placez la souris sur le membre **ViewData** pour afficher ses données.

   ![Affichez le membre ViewData de la méthode About pour voir plus d’informations](../ide/media/csharp-aspnet-home-controller-view-breakpoint-info.png)

1. Supprimez le point d’arrêt de l’application en appliquant la même méthode que celle utilisée pour l’ajouter.

1. Ouvrez *Views/Home/About.cshtml*.

   ![Sélectionnez About.cshtml dans l’Explorateur de solutions](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

1. Remplacez le texte **« additional »** par **« changed »** et enregistrez le fichier.

   ![Remplacez le texte « additional » par « changed »](../ide/media/csharp-aspnet-about-cshtml-code-change.png)

1. Revenez à la fenêtre du navigateur pour voir le texte mis à jour. (Si vous ne voyez pas le texte que vous avez modifié, actualisez le navigateur.)

    ![Actualisez la fenêtre de navigateur pour afficher le texte modifié](../ide/media/csharp-aspnet-browser-page-about-changed.png)

1. Choisissez le bouton **Arrêter le débogage** dans la barre d’outils pour arrêter le débogage. (Vous pouvez également appuyer sur **Maj**+**F5**, ou choisir **Déboguer** > **Arrêter le débogage** dans la barre de menus.)

   ![Sélectionnez le bouton Arrêter le débogage dans la barre d’outils](../ide/media/csharp-aspnet-stop-debugging.png)

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
> [Créer une application web MVC avec ASP.NET Core](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x)
>
> [!div class="nextstepaction"]
> [Créer une application web Razor Pages avec ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)

## <a name="see-also"></a>Voir aussi

[Publier une application web sur Azure App Service avec Visual Studio](..//deployment/quickstart-deploy-to-azure.md)