---
title: Bien démarrer avec ASP.NET Core
description: Cet article décrit comment démarrer avec ASP.NET dans Visual Studio pour Mac. Il couvre notamment l’installation et la création d’un projet.
author: sayedihashimi
ms.author: sayedha
ms.date: 04/02/2019
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
ms.openlocfilehash: d07849a362779f3fad8f7544899dc23b9d4538d6
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913319"
---
# <a name="getting-started-with-aspnet-core"></a>Bien démarrer avec ASP.NET Core

 Visual Studio pour Mac facilite le développement du service de votre application avec sa prise en charge pour la plateforme de développement web ASP.NET Core la plus récente. ASP.NET Core s’exécute sur .NET Core, qui est l’évolution la plus récente du .NET Framework et du runtime. Il a été optimisé pour accélérer les performances, conçu pour des tailles d’installation réduites et réinventé pour s’exécuter sur Linux et macOS, ainsi que sur Windows.

## <a name="installing-net-core"></a>Installation de .NET Core

.NET Core 2.1 est installé automatiquement quand vous installez Visual Studio pour Mac.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Création d’une application ASP.NET Core dans Visual Studio pour Mac

Ouvrez Visual Studio pour Mac. Dans l’écran de démarrage, sélectionnez **Nouveau projet...**

![Boîte de dialogue Nouveau projet](media/asp-net-core-2019-new-asp-core.png)

La boîte de dialogue Nouveau projet s’affiche et vous permet de sélectionner un modèle pour créer votre application.

Il existe un grand nombre de projets qui vous offrent un modèle prédéfini pour commencer à créer votre application ASP.NET Core. Ces règles sont les suivantes :

- **.NET Core > Vide**
- **.NET Core > API**
- **.NET Core > Application web**
- **.NET Core > Application web (modèle-vue-contrôleur)**

![Options des projets ASP.NET](media/asp-net-core-2019-new-asp-core.png)

Sélectionnez **Application web vide ASP.NET Core** et appuyez sur **Suivant**. Donnez un nom au projet et appuyez sur **Créer**. Cela crée une nouvelle ASP.NET Core application. Dans le volet gauche du panneau solution, développez la deuxième flèche, puis sélectionnez **Startup.cs**. Elle doit ressembler à l’image ci-dessous :

![Vue Nouveau projet vide ASP.NET Core](media/asp-net-core-2019-empty-project.png)

Le modèle Vide ASP.NET Core crée une application web avec deux fichiers par défaut : **Program.cs** et **Startup.cs**, qui sont décrits ci-dessous. Elle crée également un dossier de dépendances, qui contient les dépendances du package NuGet de votre projet, comme ASP.NET Core, le framework .NET Core et les cibles MSBuild qui génèrent le projet :

![Panneau Solution affichant les dépendances](media/asp-net-core-2019-solution-dependencies.png)

### <a name="programcs"></a>Program.cs

Ouvrez et examinez le fichier **Program.cs** de votre projet. Notez que plusieurs choses se produisent dans la méthode `Main`, qui est l’entrée de votre application :

```csharp
    public class Program
    {
        public static void Main(string[] args)
        {
            CreateWebHostBuilder(args).Build().Run();
        }

        public static IWebHostBuilder CreateWebHostBuilder(string[] args) =>
            WebHost.CreateDefaultBuilder(args)
                .UseStartup<Startup>();
    }
```

Une application ASP.NET Core crée un serveur web dans sa méthode main en configurant et en lançant un hôte via une instance de [ `WebHostBuilder` ](/aspnet/core/fundamentals/hosting). Ce générateur fournit des méthodes pour permettre la configuration de l’hôte. Dans le modèle d’application, les configurations suivantes sont utilisées :

* `.UseStartup<Startup>()`: Spécifie la classe de démarrage.

Toutefois, vous pouvez également ajouter des configurations supplémentaires, telles que :

* `UseKestrel`: Spécifie que le serveur Kestrel est utilisé par l’application
* `UseContentRoot(Directory.GetCurrentDirectory())`: Utilise le dossier racine du projet web comme racine du contenu de l’application quand l’application est démarrée à partir de ce dossier
* `.UseIISIntegration()`: Spécifie que l’application doit fonctionner avec IIS. Pour utiliser IIS avec ASP.NET Core, `UseKestrel` et `UseIISIntegration` doivent tous deux être spécifiés.

### <a name="startupcs"></a>Startup.cs

La classe Startup de votre application est spécifiée dans la méthode `UseStartup()` sur `CreateWebHostBuilder`. C’est dans cette classe que vous spécifiez le pipeline de gestion des demandes et où vous configurez les services.

Ouvrez et examinez le fichier **Startup.cs** de votre projet :

```csharp
    public class Startup
    {
        // This method gets called by the runtime. Use this method to add services to the container.
        // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
        public void ConfigureServices(IServiceCollection services)
        {
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app, IHostingEnvironment env)
        {
            if (env.IsDevelopment())
            {
                app.UseDeveloperExceptionPage();
            }

            app.Run(async (context) =>
            {
                await context.Response.WriteAsync("Hello World!");
            });
        }
    }
```

Cette classe Startup doit toujours respecter les règles suivantes :

- Elle doit toujours être publique.
- Elle doit contenir les deux méthodes publiques `ConfigureServices` et `Configure`.

La méthode `ConfigureServices` définit les services qui seront utilisés par votre application.

La méthode `Configure` vous permet de composer votre pipeline de demandes à l’aide de [middleware](/aspnet/core/fundamentals/middleware). Il s’agit des composants utilisés au sein d’un pipeline d’application ASP.NET pour gérer les demandes et les réponses. Le pipeline HTTP se compose d’un certain nombre de délégués de demande, appelés en séquence. Chaque délégué peut choisir de gérer la demande proprement dite ou de la passer au délégué suivant.

Vous pouvez configurer des délégués en utilisant les méthodes `Run`, `Map` et `Use` sur `IApplicationBuilder`, mais la méthode `Run` n’appelle jamais le délégué suivant et doit toujours être utilisée à la fin de votre pipeline.

La méthode `Configure` du modèle prédéfini est conçue pour effectuer certaines opérations. Elle configure d’abord une page de gestion des exceptions à utiliser pendant le développement. Ensuite, elle envoie une réponse à la page web qui fait la demande avec un simple « Hello World ».

Ce projet simple « Hello World » peut maintenant s’exécuter sans ajouter de code supplémentaire. Pour exécuter l’application et la voir dans votre navigateur, cliquez sur le bouton (triangulaire) Lecture dans la barre d’outils :

![Exécuter une application](media/asp-net-core-2019-run-debug.png)

Visual Studio pour Mac utilise un port aléatoire pour lancer votre projet web. Pour trouver de quel port il s’agit, ouvrez la sortie de l’application, qui se trouve sous **Afficher > Panneaux**. Vous devez trouver une sortie similaire à celle-ci :

![Sortie de l’application montrant le port qui est à l’écoute](media/asp-net-core-image6.png)

Une fois que le projet est en cours d’exécution, votre navigateur web par défaut doit se lancer et se connecter à l’URL figurant dans la sortie de l’application. Vous pouvez également ouvrir le navigateur de votre choix, puis entrer `http://localhost:5000/`, en remplaçant `5000` par le port indiqué par Visual Studio dans la sortie de l’application. Vous devez normalement voir le texte `Hello World!` :

![navigateur affichant le texte](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Ajour d’un contrôleur

Les applications ASP.NET Core utilisent le modèle de conception MVC (Modèle-Vue-Contrôleur) pour fournir une séparation logique entre les responsabilités de chaque partie de l’application. Le modèle MVC est constitué des éléments suivants :

- **Modèle** : Classe qui représente les données de l’application.
- **Vue** : Affiche l’interface utilisateur de l’application (qui est souvent constituée des données du modèle).
- **Contrôleur** : Classe qui gère les demandes du navigateur et qui répond aux entrées et aux interactions de l’utilisateur.

Pour plus d’informations sur l’utilisation du modèle MVC, consultez le guide [Vue d’ensemble du modèle MVC d’ASP.NET Core](/aspnet/core/mvc/overview).

Pour ajouter un contrôleur, procédez comme suit :

1. Cliquez avec le bouton droit sur le nom du projet et sélectionnez **Ajouter > Nouveaux fichiers**. Sélectionnez **Général > Classe vide**, puis entrez un nom de contrôleur :

    ![Boîte de dialogue Nouveau fichier](media/asp-net-core-image8.png)

2. Ajoutez le code suivant au nouveau contrôleur :

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using System.Text.Encodings.Web;

    namespace Hello_ASP
    {
        public class HelloWorldController : Controller
        {
            //
            // GET: /HelloWorld/

            public string Index()
            {
                return "This is my default action...";
            }

        }
    }
    ```

3. Ajoutez la dépendance `Microsoft.AspNetCore.Mvc` au projet en cliquant avec le bouton droit sur le dossier **Dépendance** et en sélectionnant **Ajouter un package...** .

4. Utilisez la zone Rechercher pour trouver `Microsoft.AspNetCore.Mvc` dans la bibliothèque NuGet, puis sélectionnez **Ajouter un package**. L’installation peut prendre quelques minutes et vous serez peut-être invité à accepter différentes licences pour les dépendances nécessaires :

    ![Ajouter NuGet](media/asp-net-core-image9.png)

5. Dans la classe Startup, supprimez l’expression lambda `app.Run` et définissez comme suit la logique de routage d’URL utilisée par MVC pour déterminer quel code il doit appeler :

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Veillez à supprimer l’expression lambda `app.Run`, car ceci remplacera la logique de routage.

    MVC utilise le format suivant pour déterminer le code à exécuter :

    `/[Controller]/[ActionName]/[Parameters]`

    Quand vous ajoutez l’extrait de code ci-dessus, vous indiquez à l’application d’utiliser par défaut le contrôleur `HelloWorld` et la méthode d’action `Index`.

6. Ajoutez l’appel de `services.AddMvc();` à la méthode `ConfigureServices`, comme illustré ci-dessous :

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    Vous pouvez également passer des informations sur les paramètres de l’URL au contrôleur.

7. Ajoutez une autre méthode à votre contrôleur HelloWorld, comme illustré ci-dessous :

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Si vous exécutez l’application maintenant, elle doit ouvrir automatiquement votre navigateur :

    ![Exécution de l’application dans le navigateur](media/asp-net-core-image13.png)

9. Essayez d’accéder à `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` (en remplaçant `xxxx` par le port approprié). Vous devez normalement voir ceci :

    ![Exécution de l’application dans le navigateur avec des arguments](media/asp-net-core-image10.png)

## <a name="troubleshooting"></a>Résolution des problèmes

Si vous devez installer .NET Core manuellement sur Mac OS 10.12 (Sierra) et ultérieur, effectuez les opérations suivantes :

1. Avant de commencer l’installation de .NET Core, assurez-vous d’avoir appliqué toutes les mises à jour du système d’exploitation à la dernière version stable. Vous pouvez le vérifier en accédant à l’application App Store et en sélectionnant l’onglet Mises à jour.

2. Suivez les étapes listées sur le [site de .NET Core](https://www.microsoft.com/net/core#macos).

Veillez à effectuer correctement toutes les étapes pour garantir que .NET Core est bien installé.

## <a name="summary"></a>Récapitulatif

Ce guide était une introduction à ASP.NET Core. Il explique ce que c’est et quand l’utiliser, et fournit des informations sur son utilisation dans Visual Studio pour Mac.
Pour plus d’informations sur les étapes à suivre à partir d’ici, consultez les guides suivants :
- Documentation [ASP.NET Core](/aspnet/core/?view=aspnetcore-2.1#build-web-apis-and-web-ui-using-aspnet-core-mvc).
- [Création de services backend pour les applications mobiles natives](/aspnet/core/mobile/native-mobile-backend), qui montre comment créer un service REST en utilisant ASP.NET Core pour une application Xamarin.Forms.
- [Ateliers pratiques ASP.NET Core](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).

## <a name="related-video"></a>Vidéo associée

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]
