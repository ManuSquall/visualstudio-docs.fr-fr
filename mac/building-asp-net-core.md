---
title: Créer des applications ASP.NET Core
description: Cet article décrit comment démarrer avec ASP.NET dans Visual Studio pour Mac. Il couvre notamment l’installation et la création d’un projet.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.openlocfilehash: 5600fd2f0b6d83a3bd27350a4d4f0137ea44ced2
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75398281"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Création d’applications ASP.NET Core dans Visual Studio pour Mac

ASP.NET Core est un framework open source et multiplateforme qui permet de créer des applications cloud modernes connectées à internet, telles que des applications et des services web, des applications IoT et des backends mobiles. Les applications ASP.NET Core peuvent s’exécuter sur le [.NET Core](https://www.microsoft.com/net/core/platform) ou sur les runtimes .NET Framework. Il a été conçu afin de fournir un framework de développement optimisée pour les applications qui sont déployées sur le cloud ou qui s’exécutent en local. Comme il est constitué de composants modulaires avec une surcharge minimale, vous pouvez construire vos solutions en toute souplesse. Vous pouvez développer et exécuter des applications multiplateformes ASP.NET Core sur Windows, Mac et Linux. ASP.NET Core est open source dans [GitHub](https://github.com/aspnet/home).

Dans ce labo, vous allez créer et explorer une application ASP.NET Core avec Visual Studio pour Mac.

## <a name="objectives"></a>Objectifs

> [!div class="checklist"]
> * Créer une application web ASP.NET Core
> * Explorer le modèle d’hébergement, de configuration et de middleware (intergiciel) d’ASP.NET Core
> * Déboguer une application web ASP.NET Core

## <a name="prerequisites"></a>Configuration requise

- [Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Public visé

Ce labo s’adresse aux développeurs qui connaissent C#. Une expérience approfondie n’est toutefois pas nécessaire.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Tâche 1 : création d’une application de ASP.NET Core

1. Lancez **Visual Studio pour Mac**.

2. Sélectionnez **Fichier > Nouvelle solution**.

3. Sélectionnez la catégorie **.NET Core > Application** et le modèle **ASP.NET Core Web App (C#)** (Application web ASP.NET Core (C#)). Cliquez sur **Next**.

    ![](media/netcore-image1.png)

4. Entrez le nom **« CoreLab »** et cliquez sur **Create** pour créer le projet. L’opération prend un certain temps.

    ![](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Tâche 2 : vélo de la solution

1. Le modèle par défaut génère une solution avec un seul projet ASP.NET Core nommé **CoreLab**. Développez le nœud de projet pour exposer son contenu.

    ![](media/netcore-image3.png)

2. Ce projet suit le paradigme modèle-vue-contrôleur (MVC) pour fournir une division claire des responsabilités entre les données (modèles), la présentation (vues) et les fonctionnalités (contrôleurs). Ouvrez le fichier **HomeController.cs** dans le dossier **Controllers**.

    ![](media/netcore-image4.png)

3. Par convention, la classe **HomeController** gère toutes les demandes entrantes qui commencent par **/Home**. La méthode **Index** gère les demandes à la racine du répertoire (par exemple, `http://site.com/Home`), tandis que les autres méthodes gèrent les demandes au niveau de leur chemin nommé en fonction de la convention, à l’image de la méthode **About()** qui gère les demandes au niveau `http://site.com/Home/About`. Bien sûr, tout ceci est configurable. **HomeController** étant le contrôleur par défaut dans un nouveau projet, les demandes à la racine du site (`http://site.com`), transitent par la méthode **Index()** de **HomeController** tout comme les demandes au niveau `http://site.com/Home` ou `http://site.com/Home/Index`.

    ![](media/netcore-image5.png)

4. Le projet a également un dossier **Views** qui contient d’autres dossiers correspondant à chaque contrôleur (et un pour les vues partagées (**Shared**)). Par exemple, le fichier CSHTML de vue (une extension du langage HTML) pour le chemin **/Home/About** se trouverait à l’emplacement **Views/Home/About.cshtml**. Ouvrez ce fichier.

    ![](media/netcore-image6.png)

5. Ce fichier CSHTML utilise la syntaxe Razor pour afficher le code HTML d’après une combinaison de balises standard et de code C# inline. Pour plus d’informations, consultez la [documentation en ligne](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

    ![](media/netcore-image7.png)

6. La solution contient également un dossier **wwwroot** qui est la racine de votre site web. Vous pouvez placer le contenu de site statique, tel que les bibliothèques JavaScript, les feuilles CSS et les images, directement aux emplacements où vous souhaiteriez qu’il soit lors du déploiement du site.

    ![](media/netcore-image8.png)

7. Il existe également plusieurs fichiers de configuration qui servent à gérer le projet, ses packages et l’application au moment de l’exécution. Par exemple, la [configuration](/aspnet/core/fundamentals/configuration) d’application par défaut est stockée dans **appsettings.json**. Le fichier appSettings. JSON imbriqué est le **appSettings. Fichier Development. JSON** . Ici, vous pouvez remplacer certains de ces paramètres en fonction de l’environnement. Visual Studio pour Mac imbriquera les fichiers de cette manière à l’aide de la même logique que Visual Studio pour Windows, de sorte que les fichiers auxquels vous devez accéder plus souvent sont au niveau de la Forefront. 

    ![](media/netcore-build-nested.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Tâche 3 : comprendre comment l’application est hébergée

1. À partir de l’**Explorateur de solutions**, ouvrez **Program.cs**. C’est le programme d’amorçage chargé d’exécuter votre application.

    ![](media/netcore-image10.png)

2. Bien que ce fichier ne contienne que deux lignes de code, celles-ci sont importantes. Nous allons les décomposer. Tout d’abord, un **WebHostBuilder** est créé. Les applications ASP.NET Core nécessitent un hôte dans lequel s’exécuter. Un hôte doit implémenter l’interface **IWebHost**, qui expose les collections des fonctionnalités et services, et une méthode **Start**. L’hôte est généralement créé à l’aide d’une instance d’un **WebHostBuilder**, qui génère et retourne une instance **WebHost**. **WebHost** référence le serveur qui gère les demandes.

    ![](media/netcore-image11.png)

3. Bien que **WebHostBuilder** soit responsable de la création de l’hôte qui amorce le serveur pour l’application, vous devez fournir un serveur qui implémente **IServer**. Par défaut, il s’agit de **[Kestrel](/aspnet/core/fundamentals/servers/kestrel)** , serveur web multiplateforme pour ASP.NET Core basé sur **libuv**, qui est une bibliothèque d’E/S asynchrones multiplateforme.

    ![](media/netcore-image12.png)

4. Ensuite, la racine du contenu du serveur est définie. Ce paramétrage détermine à quel endroit il recherche les fichiers de contenu, tels que les fichiers de vue MVC. La racine de contenu par défaut est le dossier à partir duquel l’application est exécutée.

    ![](media/netcore-image13.png)

5. Si l’application doit utiliser le serveur web Internet Information Services (IIS), la méthode **UseIISIntegration** doit être appelée dans le cadre de la génération de l’hôte. Cette méthode ne configure pas de serveur, contrairement à **UseKestrel**. Pour utiliser IIS avec ASP.NET Core, vous devez spécifier **UseKestrel** et **UseIISIntegration**. Conçu pour être exécuté derrière un proxy, **Kestrel** ne doit pas être déployé en étant directement exposé à Internet. **UseIISIntegration** spécifie IIS comme serveur proxy inverse, mais cela n’est pertinent que quand l’exécution a lieu sur des machines dotées d’IIS. Si vous déployez votre application sur Windows, laissez-l’y. Cela n’a pas d’incidence majeure.

    ![](media/netcore-image14.png)

6. Une bonne pratique consiste à séparer le chargement des paramètres de l’amorçage de l’application. Pour que cette opération soit effectuée facilement, **UseStartup** est appelée pour spécifier que la classe **Startup** doit être appelée pour le chargement des paramètres et d’autres tâches de démarrage, telles que l’insertion de middlewares dans le pipeline HTTP. Vous pouvez avoir plusieurs appels **UseStartup**, chacun d’eux remplaçant normalement les paramètres précédents en fonction des besoins.

    ![](media/netcore-image15.png)

7. La dernière étape de la création de l’interface **IWebHost** consiste à appeler **Build**.

    ![](media/netcore-image16.png)

8. Bien que des classes **IWebHost** soient requises pour implémenter la méthode **Start** non bloquante, les projets ASP.NET Core ont une méthode d’extension appelée **Run** qui wrappe **Start** avec du code bloquant ; ainsi, vous n’avez pas besoin d’empêcher manuellement la méthode de quitter immédiatement.

    ![](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Tâche 4 : exécution et débogage de l’application

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud de projet **CoreLab** et sélectionnez **Options**.

    ![](media/netcore-image18.png)

2. La boîte de dialogue **Project Options** (Options du projet) inclut tout ce dont vous avez besoin pour paramétrer la génération et l’exécution de l’application. Sélectionnez le nœud **Run > Configurations > Default** (Exécuter > Configurations > Par défaut) dans le volet gauche.

3. Cochez la case **Run on external console** (Exécuter sur la console externe) et décochez la case **Pause console output** (Suspendre la sortie de la console). En règle générale, la console de l’application auto-hébergée n’est pas visible, mais à la place l’application journalise ses résultats dans le panneau **Output** (Sortie). Dans le cadre de ce labo, nous allons également l’afficher dans une fenêtre distincte, bien que vous n’ayez pas besoin de le faire pendant un développement normal.

4. Cliquez sur **OK**.

    ![](media/netcore-image19.png)

5. Appuyez sur **F5** pour générer et exécuter l’application. Vous pouvez également sélectionner **Run > Start Debugging** (Exécuter > Démarrer le débogage).

6. Visual Studio pour Mac lance deux fenêtres. La première est une fenêtre de console qui vous donne un aperçu de l’application serveur auto-hébergée.

    ![](media/netcore-image20.png)

7. La seconde est une fenêtre de navigateur classique pour tester le site. Dans les limites des possibilités du navigateur, cette application peut être hébergée n’importe où. Cliquez sur **About** (À propos) pour accéder à cette page.

    ![](media/netcore-image21.png)

8. Entre autres choses, la page About (À propos) affiche du texte défini dans le contrôleur.

    ![](media/netcore-image22.png)

9. Gardez les deux fenêtres ouvertes et revenez à Visual Studio pour Mac. Ouvrez **Controllers/HomeController.cs** s’il n’est pas déjà ouvert.

    ![](media/netcore-image23.png)

10. Définissez un point d’arrêt sur la première ligne de la méthode **About**. Vous pouvez le faire en cliquant dans la marge ou en plaçant le curseur sur la ligne et en appuyant sur **F9**. Cette ligne définit certaines données dans la collection **ViewData** qui sont affichées dans la page CSHTML **Views/Home/About.cshtml**.

    ![](media/netcore-image24.png)

11. Revenez dans le navigateur et actualisez la page about. Cette opération déclenche le point d’arrêt dans Visual Studio pour Mac.

12. Placez le pointeur de la souris sur le membre **ViewData** pour afficher ses données. Vous pouvez également développer ses membres enfants pour voir les données imbriquées.

    ![](media/netcore-image25.png)

13. Supprimez le point d’arrêt de l’application en appliquant la même méthode que celle utilisée pour l’ajouter.

14. Ouvrez **Views/Home/About.cshtml**.

15. Remplacez le texte **« additional »** par **« changed »** et enregistrez le fichier.

    ![](media/netcore-image26.png)

16. Appuyez sur le bouton **Continue** pour poursuivre l’exécution.

    ![](media/netcore-image27.png)

17. Revenez à la fenêtre du navigateur pour voir le texte mis à jour. Cette modification peut être effectuée à tout moment, sans nécessiter systématiquement l’utilisation d’un point d’arrêt du débogueur. Actualisez le navigateur si la modification n’est pas reflétée immédiatement.

    ![](media/netcore-image28.png)

18. Fermez la fenêtre de navigateur de test et la console d’application. Cette action arrête également le débogage.

## <a name="task-5-application-startup-configuration"></a>Tâche 5 : configuration du démarrage de l’application

1. Dans l’**Explorateur de solutions**, ouvrez **Startup.cs**. Vous remarquerez peut-être des soulignements ondulés rouges pendant que les packages NuGet sont restaurés en arrière-plan et que le compilateur Roslyn génère une image complète des dépendances du projet.

    ![](media/netcore-image29.png)

2. Recherchez la méthode **Startup**. Cette section, qui définit la configuration initiale de l’application, est très fournie. Nous allons la décomposer.

    ![](media/netcore-image30.png)

3. La méthode commence par initialiser un **ConfigurationBuilder** et définir son chemin de base.

    ![](media/netcore-image31.png)

4. Ensuite, elle charge un fichier **appsettings.json** obligatoire.

    ![](media/netcore-image32.png)

5. Après cela, elle tente de charger un fichier **appsettings.json** spécifique de l’environnement, qui remplace les paramètres existants. Par exemple, voici un fichier **appsettings.Development.JSON** fourni utilisé pour l’environnement spécifié. Pour plus d’informations sur la configuration dans ASP.NET Core, consultez la [documentation](/aspnet/core/fundamentals/configuration).

    ![](media/netcore-image34.png)

6. Enfin, les variables d’environnement sont ajoutées au générateur de configuration, puis la configuration est générée et définie pour être utilisée.

    ![](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Tâche 6 : insertion d’un intergiciel d’application

1. Recherchez la méthode **Configure** dans la classe **Startup**. C’est là que sont configurés tous les middlewares afin de pouvoir être insérés dans le pipeline HTTP et utilisés pour traiter chaque demande adressée au serveur. Bien que cette méthode soit appelée une seule fois, le contenu des méthodes (telles que la méthode **UseStaticFiles**) peut être exécuté à chaque demande.

    ![](media/netcore-image36.png)

2. Vous pouvez également ajouter des middlewares à exécuter en tant que partie du pipeline. Ajoutez le code ci-dessous après **app.UseStaticFiles** pour ajouter automatiquement un en-tête **X-Test** à chaque réponse sortante. IntelliSense vous aide à compléter le code à mesure que vous le rédigez.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Appuyez sur **F5** pour générer et exécuter le projet.

4. Nous pouvons utiliser le navigateur pour inspecter les en-têtes afin de vérifier qu’ils sont ajoutés. Les instructions ci-dessous concernent Safari, mais vous pouvez faire la même opération dans [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) ou [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console).

5. Une fois que le navigateur charge le site, sélectionnez **Safari > Préférences**.

6. Sous l’onglet **Avancées**, cochez **Afficher le menu Développement dans la barre des menus**, puis fermez la boîte de dialogue.

    ![](media/netcore-image37.png)

7. Sélectionnez **Développement > Afficher les ressources de la page**.

8. Actualisez la fenêtre du navigateur afin que les outils de développement que vous venez d’ouvrir puissent effectuer le suivi du trafic et du contenu et analyser ces derniers.

9. La page HTML localhost affichée par le serveur est l’élément sélectionné par défaut.

    ![](media/netcore-image38.png)

10. Développez la **barre latérale des détails**.

    ![](media/netcore-image39.png)

11. Faites défiler l’affichage vers le bas de la barre latérale pour voir l’en-tête de réponse ajouté précédemment dans le code.

    ![](media/netcore-image40.png)

12. Fermez la fenêtre du navigateur et la console quand vous êtes satisfait.

## <a name="summary"></a>Récapitulatif

Dans ce labo, vous vous êtes initié au développement d’applications ASP.NET Core avec Visual Studio pour Mac. Si vous souhaitez explorer le développement d’une application de base de données de films plus complète, consultez le tutoriel [Bien démarrer avec ASP.NET Core MVC](/aspnet/core/tutorials/first-mvc-app/start-mvc).
