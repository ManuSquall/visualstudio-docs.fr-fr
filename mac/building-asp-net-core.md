---
title: Créer des applications ASP.NET Core
description: Cet article vous guide dans la création et l’exploration d’applications ASP.NET Core avec Visual Studio pour Mac.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.topic: how-to
ms.openlocfilehash: 22dfa4a33005afd64be54828f3b49c45244779d2
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493502"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Création d’applications ASP.NET Core dans Visual Studio pour Mac

ASP.NET Core est un framework open source et multiplateforme qui permet de créer des applications cloud modernes connectées à internet, telles que des applications et des services web, des applications IoT et des backends mobiles. Les applications ASP.NET Core peuvent s’exécuter sur le [.NET Core](https://www.microsoft.com/net/core/platform) ou sur les runtimes .NET Framework. Il a été conçu afin de fournir un framework de développement optimisée pour les applications qui sont déployées sur le cloud ou qui s’exécutent en local. Elle inclut des composants modulaires associés à des frais généraux réduits. Ainsi, vous bénéficiez d’une certaine flexibilité lors de la création de vos solutions. Vous pouvez développer et exécuter des applications multiplateformes ASP.NET Core sur Windows, Mac et Linux. ASP.NET Core est open source dans [GitHub](https://github.com/aspnet/home).

Dans ce labo, vous allez créer et explorer une application ASP.NET Core avec Visual Studio pour Mac.

## <a name="objectives"></a>Objectifs

> [!div class="checklist"]
> * Créez une application web ASP.NET Core
> * Explorer le modèle d’hébergement, de configuration et de middleware (intergiciel) d’ASP.NET Core
> * Déboguer une application web ASP.NET Core

## <a name="prerequisites"></a>Prérequis

- [Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Public concerné

Ce labo s’adresse aux développeurs qui connaissent C#. Une expérience approfondie n’est toutefois pas nécessaire.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Tâche 1 : création d’une application de ASP.NET Core

1. Lancez **Visual Studio pour Mac**.

2. Sélectionnez **Fichier > Nouvelle solution**.

3. Sélectionnez la catégorie **.NET Core > Application** et le modèle **ASP.NET Core Web App (C#)** (Application web ASP.NET Core (C#)). Cliquez sur **Suivant**.

    ![Capture d’écran montrant comment sélectionner un modèle d’application Web pour votre nouveau projet.](media/netcore-image1.png)

4. Entrez le nom **« CoreLab »** et cliquez sur **Create** pour créer le projet. L’opération prend un certain temps.

    ![Capture d’écran de la configuration de l’application Web, ajout d’un nom de projet.](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Tâche 2 : vélo de la solution

1. Le modèle par défaut génère une solution avec un seul projet ASP.NET Core nommé **CoreLab**. Développez le nœud de projet pour exposer son contenu.

    ![Capture d’écran du nœud de projet de solution sélectionné pour afficher son contenu, y compris les dossiers et les fichiers.](media/netcore-image3.png)

2. Ce projet suit le paradigme modèle-vue-contrôleur (MVC) pour fournir une division claire des responsabilités entre les données (modèles), la présentation (vues) et les fonctionnalités (contrôleurs). Ouvrez le fichier **HomeController.cs** dans le dossier **Controllers**.

    ![Capture d’écran du projet de solution avec une classe C# nommée HomeController sélectionnée.](media/netcore-image4.png)

3. Par convention, la classe **HomeController** gère toutes les demandes entrantes qui commencent par **/Home**. La méthode **Index** gère les demandes à la racine du répertoire (par exemple, `http://site.com/Home`), tandis que les autres méthodes gèrent les demandes au niveau de leur chemin nommé en fonction de la convention, à l’image de la méthode **About()** qui gère les demandes au niveau `http://site.com/Home/About`. Bien sûr, tout ceci est configurable. **HomeController** étant le contrôleur par défaut dans un nouveau projet, les demandes à la racine du site (`http://site.com`), transitent par la méthode **Index()** de **HomeController** tout comme les demandes au niveau `http://site.com/Home` ou `http://site.com/Home/Index`.

    ![Capture d’écran d’une classe C# nommée HomeController.](media/netcore-image5.png)

4. Le projet a également un dossier **Views** qui contient d’autres dossiers correspondant à chaque contrôleur (et un pour les vues partagées ( **Shared** )). Par exemple, le fichier CSHTML de vue (une extension du langage HTML) pour le chemin **/Home/About** se trouverait à l’emplacement **Views/Home/About.cshtml**. Ouvrez ce fichier.

    ![Capture d’écran du projet de solution avec le fichier C S H T M L nommé about Selected.](media/netcore-image6.png)

5. Ce fichier CSHTML utilise la syntaxe Razor pour afficher le code HTML d’après une combinaison de balises standard et de code C# inline. Pour plus d’informations, consultez la [documentation en ligne](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

    ![Capture d’écran de la partie d’un fichier C S H T M L montrant syntaxe Razor.](media/netcore-image7.png)

6. La solution contient également un dossier **wwwroot** qui est la racine de votre site web. Vous pouvez placer le contenu de site statique, tel que les bibliothèques JavaScript, les feuilles CSS et les images, directement aux emplacements où vous souhaiteriez qu’il soit lors du déploiement du site.

    ![Capture d’écran de la solution avec le dossier racine w w w sélectionné.](media/netcore-image8.png)

7. Il existe également plusieurs fichiers de configuration qui servent à gérer le projet, ses packages et l’application au moment de l’exécution. Par exemple, la [configuration](/aspnet/core/fundamentals/configuration) d’application par défaut est stockée dans **appsettings.json**. Le **appsettings.Development.jsdans** le fichier est imbriqué sous le appsettings.jsfichier. Ici, vous pouvez remplacer certains de ces paramètres en fonction de l’environnement. Visual Studio pour Mac imbriquera les fichiers de cette manière à l’aide de la même logique que Visual Studio pour Windows, de sorte que les fichiers auxquels vous devez accéder plus souvent sont au niveau de la Forefront. 

    ![Capture d’écran montrant une vue détaillée avec un fichier JSON sélectionné.](media/netcore-build-nested.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Tâche 3 : comprendre comment l’application est hébergée

1. À partir de l’ **Explorateur de solutions** , ouvrez **Program.cs**. C’est le programme d’amorçage chargé d’exécuter votre application.

    ![Capture d’écran de la solution avec le fichier source C# nommé programme sélectionné.](media/netcore-image10.png)

2. Bien que ce fichier ne contienne que deux lignes de code, celles-ci sont importantes. Nous allons les décomposer. Tout d’abord, un **WebHostBuilder** est créé. Les applications ASP.NET Core nécessitent un hôte dans lequel s’exécuter. Un hôte doit implémenter l’interface **IWebHost** , qui expose les collections des fonctionnalités et services, et une méthode **Start**. L’hôte est généralement créé à l’aide d’une instance d’un **WebHostBuilder** , qui génère et retourne une instance **WebHost**. **WebHost** référence le serveur qui gère les demandes.

    ![Capture d’écran de la méthode main C# avec une instruction qui initialise une variable nommée Host avec le type WebHostBuilder.](media/netcore-image11.png)

3. Alors que **WebHostBuilder** est responsable de la création de l’hôte qui va amorcer le serveur pour l’application, vous devez fournir un serveur qui implémente **`IServer`** . Par défaut, il s’agit de **[Kestrel](/aspnet/core/fundamentals/servers/kestrel)** , serveur web multiplateforme pour ASP.NET Core basé sur **libuv** , qui est une bibliothèque d’E/S asynchrones multiplateforme.

    ![Capture d’écran de la méthode main C# en mettant en surbrillance la variable hôte en définissant le serveur avec la méthode UseKestrel.](media/netcore-image12.png)

4. Ensuite, la racine du contenu du serveur est définie. Ce paramétrage détermine à quel endroit il recherche les fichiers de contenu, tels que les fichiers de vue MVC. La racine de contenu par défaut est le dossier à partir duquel l’application est exécutée.

    ![Capture d’écran de la méthode main C# en mettant en surbrillance la variable hôte en définissant la racine de contenu pour le serveur avec la méthode UseContentRoot.](media/netcore-image13.png)

5. Si l’application doit utiliser le serveur web Internet Information Services (IIS), la méthode **UseIISIntegration** doit être appelée dans le cadre de la génération de l’hôte. Cette méthode ne configure pas de serveur, contrairement à **UseKestrel**. Pour utiliser IIS avec ASP.NET Core, vous devez spécifier **UseKestrel** et **UseIISIntegration**. Conçu pour être exécuté derrière un proxy, **Kestrel** ne doit pas être déployé en étant directement exposé à Internet. **UseIISIntegration** spécifie IIS comme serveur proxy inverse, mais cela n’est pertinent que quand l’exécution a lieu sur des machines dotées d’IIS. Si vous déployez votre application sur Windows, laissez-l’y. Cela n’a pas d’incidence majeure.

    ![Capture d’écran de la méthode main C# en mettant en surbrillance la variable hôte en définissant le serveur proxy inverse avec la méthode UseIISIntegration.](media/netcore-image14.png)

6. Une bonne pratique consiste à séparer le chargement des paramètres de l’amorçage de l’application. Pour que cette opération soit effectuée facilement, **UseStartup** est appelée pour spécifier que la classe **Startup** doit être appelée pour le chargement des paramètres et d’autres tâches de démarrage, telles que l’insertion de middlewares dans le pipeline HTTP. Vous pouvez avoir plusieurs appels **UseStartup** , chacun d’eux remplaçant normalement les paramètres précédents en fonction des besoins.

    ![Capture d’écran de la méthode main C# mise en surbrillance de la variable hôte définition de la classe Startup avec l’option UseStartup](media/netcore-image15.png)

7. La dernière étape de la création de l’interface **IWebHost** consiste à appeler **Build**.

    ![Capture d’écran de la méthode main C# mettant en surbrillance la variable hôte avec la méthode de génération.](media/netcore-image16.png)

8. Bien que des classes **IWebHost** soient requises pour implémenter la méthode **Start** non bloquante, les projets ASP.NET Core ont une méthode d’extension appelée **Run** qui wrappe **Start** avec du code bloquant ; ainsi, vous n’avez pas besoin d’empêcher manuellement la méthode de quitter immédiatement.

    ![Capture d’écran de la méthode main C# mettant en évidence le point d’hôte d’instruction.](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Tâche 4 : exécution et débogage de l’application

1. Dans l’ **Explorateur de solutions** , cliquez avec le bouton droit sur le nœud de projet **CoreLab** et sélectionnez **Options**.

    ![Capture d’écran montrant le menu contextuel de la solution CoreLab, options de surbrillance.](media/netcore-image18.png)

2. La boîte de dialogue **Project Options** (Options du projet) inclut tout ce dont vous avez besoin pour paramétrer la génération et l’exécution de l’application. Sélectionnez le nœud **Run > Configurations > Default** (Exécuter > Configurations > Par défaut) dans le volet gauche.

3. Cochez la case **Run on external console** (Exécuter sur la console externe) et décochez la case **Pause console output** (Suspendre la sortie de la console). Normalement, la console de l’application auto-hébergée n’est pas visible, mais les résultats sont consignés dans la fenêtre **sortie** . Dans le cadre de ce labo, nous allons également l’afficher dans une fenêtre distincte, bien que vous n’ayez pas besoin de le faire pendant un développement normal.

4. Cliquez sur **OK**.

    ![Capture d’écran montrant l’onglet général de la configuration de série de tests avec l’option exécuter sur la console externe sélectionnée et suspendre la sortie de la console non sélectionnée.](media/netcore-image19.png)

5. Appuyez sur **F5** pour générer et exécuter l’application. Vous pouvez également sélectionner **Run > Start Debugging** (Exécuter > Démarrer le débogage).

6. Visual Studio pour Mac lance deux fenêtres. La première est une fenêtre de console qui vous donne un aperçu de l’application serveur auto-hébergée.

    ![Capture d’écran montrant la fenêtre de console pour l’application serveur auto-hébergée.](media/netcore-image20.png)

7. La seconde est une fenêtre de navigateur classique pour tester le site. Dans les limites des possibilités du navigateur, cette application peut être hébergée n’importe où. Cliquez sur **About** (À propos) pour accéder à cette page.

    ![Capture d’écran montrant une fenêtre de navigateur pour tester le site, en mettant en surbrillance l’option à propos de.](media/netcore-image21.png)

8. Entre autres choses, la page About (À propos) affiche du texte défini dans le contrôleur.

    ![Capture d’écran montrant le résultat de la sélection de l’option à propos de, qui est une page à propos de.](media/netcore-image22.png)

9. Gardez les deux fenêtres ouvertes et revenez à Visual Studio pour Mac. Ouvrez **Controllers/HomeController.cs** s’il n’est pas déjà ouvert.

    ![Capture d’écran montrant la solution à l’aide de la classe HomeController C# sélectionnée.](media/netcore-image23.png)

10. Définissez un point d’arrêt sur la première ligne de la méthode **About**. Vous pouvez le faire en cliquant dans la marge ou en plaçant le curseur sur la ligne et en appuyant sur **F9**. Cette ligne définit certaines données dans la collection **ViewData** qui sont affichées dans la page CSHTML **Views/Home/About.cshtml**.

    ![Capture d’écran montrant la méthode about avec un point d’arrêt défini.](media/netcore-image24.png)

11. Revenez dans le navigateur et actualisez la page about. Cette opération déclenche le point d’arrêt dans Visual Studio pour Mac.

12. Placez le pointeur de la souris sur le membre **ViewData** pour afficher ses données. Vous pouvez également développer ses membres enfants pour voir les données imbriquées.

    ![Capture d’écran montrant un point d’arrêt avec ses données développées.](media/netcore-image25.png)

13. Supprimez le point d’arrêt de l’application en appliquant la même méthode que celle utilisée pour l’ajouter.

14. Ouvrez **Views/Home/About.cshtml**.

15. Remplacez le texte **« additional »** par **« changed »** et enregistrez le fichier.

    ![Capture d’écran du fichier C S H T M L nommé about avec une modification apportée à son texte.](media/netcore-image26.png)

16. Appuyez sur le bouton **Continue** pour poursuivre l’exécution.

    ![Capture d’écran de la fenêtre Visual Studio mettant en surbrillance le bouton continuer.](media/netcore-image27.png)

17. Revenez à la fenêtre du navigateur pour voir le texte mis à jour. Cette modification peut être effectuée à tout moment, sans nécessiter systématiquement l’utilisation d’un point d’arrêt du débogueur. Actualisez le navigateur si la modification n’est pas reflétée immédiatement.

    ![Capture d’écran de la page about, cette fois avec le texte modifié.](media/netcore-image28.png)

18. Fermez la fenêtre de navigateur de test et la console d’application. Cette action arrête également le débogage.

## <a name="task-5-application-startup-configuration"></a>Tâche 5 : configuration du démarrage de l’application

1. Dans l’ **Explorateur de solutions** , ouvrez **Startup.cs**. Vous remarquerez peut-être des soulignements ondulés rouges pendant que les packages NuGet sont restaurés en arrière-plan et que le compilateur Roslyn génère une image complète des dépendances du projet.

    ![Capture d’écran de la solution avec le fichier de classe C# nommé Startup Selected.](media/netcore-image29.png)

2. Recherchez la méthode **Startup**. Cette section, qui définit la configuration initiale de l’application, est très fournie. Nous allons la décomposer.

    ![Capture d’écran montrant la méthode de démarrage de la classe Startup.](media/netcore-image30.png)

3. La méthode commence par initialiser un **ConfigurationBuilder** et définir son chemin de base.

    ![Capture d’écran de la méthode Startup, montrant une instruction initialisant une variable nommée Builder avec le type ConfigurationBuilder.](media/netcore-image31.png)

4. Ensuite, elle charge un fichier **appsettings.json** obligatoire.

    ![Capture d’écran de la méthode Startup, montrant la variable de générateur à l’aide de la méthode AddJsonFile pour ajouter le fichier JSON nommé appSettings.](media/netcore-image32.png)

5. Après cela, elle tente de charger un fichier **appsettings.json** spécifique de l’environnement, qui remplace les paramètres existants. Par exemple, voici un fichier **appsettings.Development.JSON** fourni utilisé pour l’environnement spécifié. Pour plus d’informations sur la configuration dans ASP.NET Core, consultez la [documentation](/aspnet/core/fundamentals/configuration).

    ![Capture d’écran de la méthode Startup, montrant la variable de générateur à l’aide de la méthode AddJsonFile pour ajouter un fichier JSON JSON spécifique à l’environnement.](media/netcore-image34.png)

6. Enfin, les variables d’environnement sont ajoutées au générateur de configuration, puis la configuration est générée et définie pour être utilisée.

    ![Capture d’écran de la méthode Startup, montrant la variable de générateur ajout de variables d’environnement, puis utilisation de la méthode de génération pour générer la configuration.](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Tâche 6 : insertion d’un intergiciel d’application

1. Recherchez la méthode **Configure** dans la classe **Startup**. C’est là que sont configurés tous les middlewares afin de pouvoir être insérés dans le pipeline HTTP et utilisés pour traiter chaque demande adressée au serveur. Bien que cette méthode soit appelée une seule fois, le contenu des méthodes (telles que la méthode **UseStaticFiles** ) peut être exécuté à chaque demande.

    ![Capture d’écran montrant la méthode configure de la classe Startup.](media/netcore-image36.png)

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

6. Sous l’onglet **Avancées** , cochez **Afficher le menu Développement dans la barre des menus** , puis fermez la boîte de dialogue.

    ![Capture d’écran montrant le volet avancé dans la boîte de dialogue Préférences de Safari avec l’option Afficher le menu développer dans la barre de menus sélectionnée.](media/netcore-image37.png)

7. Sélectionnez **Développement > Afficher les ressources de la page**.

8. Actualisez la fenêtre du navigateur afin que les outils de développement que vous venez d’ouvrir puissent effectuer le suivi du trafic et du contenu et analyser ces derniers.

9. La page HTML localhost affichée par le serveur est l’élément sélectionné par défaut.

    ![Capture d’écran mettant en surbrillance la page localhost H T M L.](media/netcore-image38.png)

10. Développez la **barre latérale des détails**.

    ![Capture d’écran mettant en surbrillance le contrôle à utiliser pour développer la barre latérale des détails.](media/netcore-image39.png)

11. Faites défiler l’affichage vers le bas de la barre latérale pour voir l’en-tête de réponse ajouté précédemment dans le code.

    ![Capture d’écran mettant en surbrillance l’en-tête de réponse nommé XTest avec une valeur de test.](media/netcore-image40.png)

12. Fermez la fenêtre du navigateur et la console quand vous êtes satisfait.

## <a name="summary"></a>Résumé

Dans ce labo, vous vous êtes initié au développement d’applications ASP.NET Core avec Visual Studio pour Mac. Si vous souhaitez explorer le développement d’une application de base de données de films plus complète, consultez le tutoriel [Bien démarrer avec ASP.NET Core MVC](/aspnet/core/tutorials/first-mvc-app/start-mvc).
