---
title: 'Étape 2 : Créer votre première application Web ASP.NET'
description: Créez votre première application web ASP.NET Core avec ce tutoriel vidéo et des instructions détaillées.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 1d382e83aa9672cfdcbdca64b89be79d090f2aac
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580076"
---
# <a name="step-2-create-your-first-aspnet-core-web-app"></a>Étape 2 : Créez votre première application web ASP.NET Core

Créez votre première application web ASP.NET Core avec ce tutoriel vidéo et des instructions détaillées.

_Regardez cette vidéo et suivez la procédure pour créer votre première application ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/-79RkpyFB6E]

## <a name="start-visual-studio-2019-and-create-a-new-project"></a>Démarrer Visual Studio 2019 et créer un projet

Démarrez Visual Studio 2019 et cliquez sur **Créer un projet**. Choisissez **Application web ASP.NET Core**. Choisissez le modèle **Application web** et gardez le nom et l’emplacement par défaut du projet. Dans le dropdown avec la version ASP.NET Core, choisissez **ASP.NET Core 2.1** ou **ASP.NET Core 2.2**. Cliquez sur **Créer**. Pour obtenir des instructions plus précises, reportez-vous à [la vidéo précédente de cette série de tutoriels](tutorial-aspnet-core-ef-step-01.md).

![Visual Studio 2019 – Choisir les options de projet ASP.NET Core](media/vs-2019/vs2019-choose-aspnetcore-project.png)

> [!WARNING]
> Assurez-vous de choisir ASP .NET Core 2.1 ou ASP.NET Core 2.2. Ce tutoriel n’est pas compatible avec ASP.NET Core 3.x.

## <a name="explore-the-new-project"></a>Explorer le nouveau projet

Dans la fenêtre Explorateur de solutions située à droite, vous pouvez voir le contenu du nouveau projet. C’est ici qu’il est décrit.

![Projet ASP.NET Core Visual Studio 2019](media/vs-2019/vs2019-solution-explorer.png)

### <a name="wwwroot"></a>wwwroot

Le dossier *wwwroot* contient des fichiers statiques publiquement accessibles à partir de l’application web. Il contient généralement des feuilles de style, des fichiers de script côté client et des images.

### <a name="pages"></a>Pages

Le dossier *Pages* contient la solution Razor Pages du site. Le modèle par défaut fournit plusieurs pages, notamment la page *Index.cshtml* qui est la page d’accueil de l’application, ainsi que les pages About, Contact, etc.

### <a name="appsettingsjson"></a>appsettings.json

Ce fichier contient les paramètres de configuration du site, au format JSON.

### <a name="programcs"></a>Program.cs

Ce fichier joue le rôle de point d’entrée de l’application. Quand l’application est exécutée, sa méthode Main est la première méthode qui est exécutée. Elle se charge de créer l’hôte web qui va contenir l’application.

### <a name="startupcs"></a>Startup.cs

L’hôte web créé dans *Program.cs* fait référence à la classe Startup et appelle ses méthodes pour configurer l’application. La méthode ConfigureServices se charge de configurer tous les services que l’application va utiliser. La méthode `Configure` configure le pipeline de requête HTTP de l’application. Chaque requête passe par ce pipeline, en interagissant avec chaque élément du *middleware (intergiciel)* par la même occasion.

### <a name="indexcshtml"></a>Index.cshtml

La page d’accueil du site inclut des balises HTML et du code Razor côté serveur. Elle utilise Razor pour spécifier le modèle de page, `IndexModel`, qui se trouve dans le fichier *Index.cshtml.cs* associé. Elle définit également le titre de la page en définissant une valeur dans ViewData. Cette valeur ViewData est lue dans le * \_fichier Layout.cshtml,* situé dans le dossier partagé à l’intérieur du dossier Pages. Le fichier Layout est partagé par de nombreuses Razor Pages et fournit l’aspect commun de l’application. Le contenu de chaque page est rendu dans le code HTML du fichier Layout.

## <a name="run-the-application"></a>Exécuter l’application

Exécutez à présent l’application pour la voir dans le navigateur. Vous pouvez exécuter l’application à l’aide **de Ctrl**+**F5** ou en choisissant **Debug** > **Start Without Debugging** dans le menu de Visual Studio.

## <a name="customize-the-application"></a>Personnaliser l’application

Ajoutez une propriété au fichier *Index.cshtml.cs* et affectez-lui la valeur de l’heure actuelle dans le gestionnaire `OnGet` :

```csharp
public string Time { get; set; }
public void OnGet()
{
    Time = DateTime.Today.ToShortTimeString();
}
```

Remplacez le contenu de `<div>` dans *Index.cshtml* par cette balise :

```cshtml
<h2>It's @Model.Time right now on the server!</h2>
```

Exécutez de nouveau l'application. Vous devez maintenant voir que la page affiche l’heure actuelle, mais qu’il est toujours minuit ! Cela ne va pas.

![Projet ASP.NET Core Visual Studio 2019 dans le navigateur](media/vs-2019/vs2019-app-in-browser.png)

## <a name="debug-the-application"></a>Déboguer l’application

Ajoutez un point d’arrêt à la méthode `OnGet` où nous affectons une valeur à `Time` et cette fois, commencez à déboguer l’application.

L’exécution s’arrête sur la ligne et vous pouvez voir que `DateTime.Today` inclut la date, mais que l’heure est toujours minuit, car aucune donnée d’heure n’est incluse. 

![Projet ASP.NET Core Visual Studio 2019 dans le navigateur](media/vs-2019/vs2019-breakpoint.png)

Remplacez-le par `DateTime.Now` et continuez l’exécution. Le nouveau code pour `OnGet` doit être :

```csharp
public void OnGet()
{
    Time = DateTime.Now.ToShortTimeString();
}
```

Vous devez maintenant voir l’heure réelle du serveur dans le navigateur quand vous accédez à l’application.

> [!NOTE]
> Votre sortie peut différer de l’image, dans la mesure où le format de sortie de ToShortDateTimeString varie selon le paramètre de culture actuel. Consultez <xref:System.DateTime.ToShortTimeString>.

![Projet ASP.NET Core Visual Studio 2019 dans le navigateur](media/vs-2019/vs2019-app-fixed-in-browser.png)

## <a name="next-steps"></a>Étapes suivantes

Dans la vidéo suivante, vous allez apprendre à ajouter la prise en charge de données à votre application.

[Tutorial: Travailler avec des données dans votre application de base ASP.NET](tutorial-aspnet-core-ef-step-03.md)

## <a name="see-also"></a>Voir aussi

- [Tutorial: Créer une application Web Razor Pages avec ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)
