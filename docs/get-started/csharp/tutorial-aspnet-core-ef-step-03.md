---
title: 'Étape 3 : Utiliser des données dans une application ASP.NET Core'
description: Commencez à travailler avec les données à l’aide d’Entity Framework Core dans votre application web ASP.NET Core avec ce tutoriel vidéo et des instructions détaillées.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: c1d95d7621a97a36fdf737e7d3dd4f8baf713645
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553951"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>Étape 3 : Travailler avec des données à l’aide d’Entity Framework

Suivez ces étapes pour commencer à travailler avec des données à l’aide d’Entity Framework Core dans votre application web ASP.NET Core.

_Regardez cette vidéo et suivez la procédure pour ajouter des données à votre première application ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>Ouvrir le projet

Si vous avez suivi ces vidéos, ouvrez le projet d’application web que vous avez créé dans la section précédente. Si vous commencez ici, créez un projet et choisissez **Application web ASP.NET**, puis **Application web**. Conservez les autres options par défaut.

## <a name="add-your-model"></a>Ajouter un modèle

La première chose à faire pour travailler avec des données dans une application ASP.NET Core est de décrire leur format. Nous appelons cela créer un *modèle* des différents aspects du problème à résoudre. Dans des applications réelles, il s’agirait d’ajouter une logique métier personnalisée à ces modèles pour leur imposer un certain comportement et automatiser les tâches. Dans cet exemple, nous allons créer un système simple de suivi de jeux de société. Il nous faut une classe qui représente un jeu et comprenne les propriétés à enregistrer sur ce jeu, comme le nombre de joueurs possibles. Cette classe se trouvera dans un nouveau dossier, nommé *Models*, créé à la racine du projet web.

```csharp
public class Game
{
    public int Id { get; set; }
    public string Title { get; set; }
    public int PublicationYear { get; set; }
    public int MinimumPlayers { get; set; }
    public int MaximumPlayers { get; set; }
}
```

## <a name="create-the-pages-to-manage-your-game-library"></a>Créer les pages pour gérer la bibliothèque de jeux

Nous sommes maintenant prêts à créer les pages qui serviront à gérer notre bibliothèque de jeux. Si l’entreprise peut sembler colossale, elle est en fait extrêmement simple. Nous devons d’abord décider où devra se trouver cette fonctionnalité dans notre application. Ouvrez le dossier Pages dans le projet web et ajoutez-y un nouveau dossier. Appelez-le *Games*.

Maintenant, cliquez avec le bouton droit sur Games et choisissez **Ajouter** > **Nouvel élément généré automatiquement**. Choisissez Razor Pages avec l’option **Entity Framework (CRUD)**. CRUD signifie « create, read, update, delete » pour « créer, lire, mettre à jour, supprimer » ; ce modèle créera des pages pour chacune de ces opérations (y compris une page « Tout lister » et une page « Afficher les détails d’un élément »).

![Visual Studio 2019 ASP.NET Core – Ajouter des pages générées automatiquement](media/vs-2019/vs2019-add-scaffold.png)

Sélectionnez votre classe de modèle Game et utilisez l’icône « + » pour ajouter une nouvelle classe de contexte de données. Nommez-le `AppDbContext`. Laissez les autres options par défaut et cliquez sur **Ajouter**.

Les pages Razor Pages suivantes sont ajoutées à votre dossier Games :

- Create.cshtml
- Delete.cshtml
- Details.cshtml
- Edit.cshtml
- Index.cshtml

![Visual Studio 2019 ASP.NET Core – Pages générées automatiquement](media/vs-2019/vs2019-scaffolded-pages.png)

L’opération de génération automatique a ajouté non seulement des pages au dossier *Games*, mais aussi du code à la classe *Startup.cs*. Dans la méthode `ConfigureServices` de cette classe, on constate ce code a été ajouté :

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

La chaîne de connexion `AppDbContext` a également été ajoutée au fichier *appsettings.json* du projet.

Si vous exécutez l’application maintenant, il y a un risque d’échec, car aucune base de données n’a encore été créée. Vous pouvez configurer l’application de sorte qu’elle crée automatiquement la base de données si nécessaire par [ajout de code à Program.cs](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio#update-main) :

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<SchoolContext>();
            context.Database.EnsureCreated();
        }
        catch (Exception ex)
        {
            var logger = services.GetRequiredService<ILogger<Program>>();
            logger.LogError(ex, "An error occurred creating the DB.");
        }
    }

    host.Run();
}
```

La majeure partie du code concerne simplement la gestion des erreurs et l’accès à EF Core `AppDbContext` avant l’exécution de l’application. La ligne importante est `context.Database.EnsureCreated()`, qui crée la base de données si elle n’existe pas déjà. L’application est maintenant prête à s’exécuter.

## <a name="test-it-out"></a>Tester

Exécutez l’application et accédez à `/Games` dans la barre d’adresse. Une page comportant une liste vide apparaît. Cliquez sur **Créer** pour ajouter un nouveau `Game` à la collection. Remplissez le formulaire et cliquez sur **Créer**. Il devrait apparaître dans le mode Liste. Cliquez sur **Détails** pour voir les détails d’un enregistrement.

Ajoutez un autre enregistrement. Vous pouvez cliquer sur *Modifier* pour modifier les détails d’un enregistrement, ou sur **Supprimer** pour le supprimer (après confirmation dans une invite).

![Visual Studio 2019 ASP.NET Core – Pages générées automatiquement dans le navigateur](media/vs-2019/vs2019-game-list.png)

Il n’y a rien d’autre à faire pour commencer à travailler avec des données dans une application ASP.NET Core à l’aide d’EF Core et de Visual Studio 2019.

## <a name="next-steps"></a>Étapes suivantes

Dans la vidéo suivante, vous allez apprendre à ajouter la prise en charge de l’API web à votre application.

[Étape 4 : Exposer une API web à partir d’une application ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>Voir aussi

- [Razor Pages avec Entity Framework Core dans ASP.NET Core](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio)
- [Razor Pages ASP.NET Core avec EF Core](/aspnet/core/data/?view=aspnetcore-2.1)
