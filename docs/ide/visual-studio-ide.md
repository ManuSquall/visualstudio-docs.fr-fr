---
title: Vue d’ensemble de Visual Studio 2017
ms.date: 06/01/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- MSDNSTART
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a7667cac2a26a3e98d2e92dfeb13cee36d870e9
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34691158"
---
# <a name="visual-studio-ide-overview"></a>Vue d’ensemble de l’IDE de Visual Studio

L’environnement de développement interactif (IDE) de Visual Studio est une plateforme de lancement créative avec laquelle vous pouvez afficher et modifier du code, puis déboguer, générer et publier des applications.

Visual Studio est disponible pour Windows et Mac. [Visual Studio pour Mac](/visualstudio/mac/) compte de nombreuses fonctionnalités en commun avec Visual Studio 2017, et est optimisé pour le développement d’applications mobiles et multiplateformes.

Cet article se concentre sur Visual Studio 2017 pour Windows. Il vous présente les fonctionnalités de base de l’IDE. Nous allons voir en détail certaines opérations que vous pouvez effectuer avec Visual Studio, notamment la création d’un projet simple, l’utilisation d’IntelliSense comme une aide au codage et le débogage d’une application pour afficher la valeur d’une variable pendant l’exécution du programme. Nous allons également effectuer une visite guidée des différentes fenêtres Outil.

## <a name="install-the-visual-studio-ide"></a>Installer l’IDE de Visual Studio

Pour commencer, [téléchargez Visual Studio 2017](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) et installez-le sur votre système.

Le programme d’installation modulaire vous permet de choisir et d’installer des *charges de travail*, qui sont des groupes de fonctionnalités requises pour la plateforme ou le langage de programmation de votre choix. Pour suivre les étapes de [création d’un programme](#create-a-program), veillez à sélectionner la charge de travail **Développement multiplateforme .NET Core** pendant l’installation. Les rubriques de démarrage rapide, comme [Bien démarrer avec C++ dans Visual Studio](getting-started-with-cpp-in-visual-studio.md), contiennent des instructions sur l’installation d’autres charges de travail.

![Programme d’installation de Visual Studio](../ide/media/overview-net-core-workload.png)

Quand vous démarrez Visual Studio pour la première fois, vous pouvez vous connecter avec votre compte Microsoft, ou avec votre compte professionnel ou celui de votre établissement scolaire.

## <a name="tour-of-the-ide"></a>Visite guidée de l’IDE

Pour vous donner une représentation générale de Visual Studio, l’image suivante montre un projet ouvert dans Visual Studio et les fenêtres Outil principales dont vous aurez probablement besoin :

![IDE de Visual Studio](../ide/media/visualstudioide.png)

- L’[Explorateur de solutions](../ide/solutions-and-projects-in-visual-studio.md) vous permet d’afficher, de parcourir et de gérer vos fichiers de code. L’Explorateur de solutions peut vous aider à organiser votre code en regroupant les fichiers dans des projets et des solutions.

- La fenêtre de l’[éditeur](../ide/writing-code-in-the-code-and-text-editor.md) est la fenêtre où vous passerez sans doute le plus de temps. Utilisez cette fenêtre pour afficher votre code, modifier le code source et concevoir une interface utilisateur.

- La [fenêtre Sortie](../ide/reference/output-window.md) est l’emplacement où Visual Studio envoie ses notifications, comme les messages d’erreur et de débogage, les avertissements du compilateur, les messages d’état de publication, entre autres. Chaque source de message a son propre onglet.

- [Team Explorer (VSTS)](/vsts/user-guide/work-team-explorer) vous permet de suivre des éléments de travail et de partager du code avec d’autres utilisateurs à l’aide des technologies de gestion de versions comme [Git](https://git-scm.com/) et [Team Foundation Version Control (TFVC)](/vsts/tfvc/overview).

Voici d’autres fonctionnalités de productivité très utilisées de Visual Studio :

- La [refactorisation](../ide/refactoring-in-visual-studio.md) inclut des opérations comme le renommage intelligent des variables, le déplacement de lignes de code sélectionnées dans une fonction distincte, le déplacement de code à d’autres endroits, la réorganisation des paramètres des fonctions, et ainsi de suite.

   ![Refactorisation](../ide/media/VSIDE_refactor.png)

- [IntelliSense](../ide/using-intellisense.md) est un terme couvrant un ensemble de fonctionnalités appréciées qui affichent des informations sur les types concernant votre code directement dans l’éditeur et qui, dans certains cas, écrivent de petits extraits de code pour vous. Cela revient à avoir de la documentation de base incluse dans l’éditeur, ce qui vous évite d’avoir à rechercher des informations sur les types dans une fenêtre d’aide distincte. Les fonctionnalités d'IntelliSense varient selon le langage. Pour plus d’informations, consultez [C# IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md) et [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md). L’illustration suivante montre certaines fonctionnalités IntelliSense à l'œuvre :

   ![Liste des membres Visual Studio](../ide/media/vs2017_Intellisense.png)

- La zone de recherche [Lancement rapide](../ide/reference/quick-launch-environment-options-dialog-box.md) est un excellent moyen de trouver rapidement ce dont vous avez besoin dans Visual Studio. Commencez simplement par taper le nom de l’élément que vous recherchez. Visual Studio affiche alors les résultats de la recherche à partir desquels vous pouvez accéder à l’élément précis recherché. Le **lancement rapide** affiche également des liens permettant de démarrer **Visual Studio Installer** pour une charge de travail ou un composant individuel.

   ![Zone de recherche de lancement rapide](../ide/media/VSIDE_Tour_QuickLaunch.png)

- Les **tildes** sont des soulignements ondulés qui vous signalent des erreurs ou des problèmes potentiels dans votre code en temps réel en cours de frappe. Cela vous permet de les corriger immédiatement sans attendre la détection de l’erreur lors de la compilation ou de l’exécution. Si vous pointez sur le tilde, vous voyez des informations supplémentaires sur l'erreur. Une ampoule peut également apparaître dans la marge gauche, avec des actions pour corriger l’erreur. Pour plus d’informations, consultez [Actions rapides](../ide/quick-actions.md).

   ![Tildes](../ide/media/vs2017_squiggle.png)

- Vous pouvez ouvrir la fenêtre [Hiérarchie d’appels](../ide/reference/call-hierarchy.md) dans le menu contextuel de l’éditeur de texte pour afficher les méthodes qui appellent la méthode sous le signe insertion (point d’insertion) et qui sont appelées par cette méthode.

   ![Fenêtre Hiérarchie d'appels](../ide/media/VSIDE_call_hierarchy.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) vous permet de rechercher les références et les modifications apportées à votre code, les bogues liés, les éléments de travail, les révisions de code et les tests unitaires, tout cela sans quitter l'éditeur.

   ![CodeLens](../ide/media/codelensoverview.png)

- La fenêtre [Aperçu de la définition](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) montre une définition de méthode ou de type inline, sans vous obliger à quitter votre contexte actuel.

   ![Aperçu de définition](../ide/media/VSIDE_peek_definition.png)

- L'option de menu contextuel [Atteindre la définition](../ide/go-to-and-peek-definition.md) vous amène directement à l'endroit où la fonction ou l'objet est défini. D'autres commandes de navigation sont également disponibles en cliquant avec le bouton droit dans l'éditeur.

   ![Atteindre la définition](../ide/media/VSIDE_go_to_definition.png)

## <a name="create-a-program"></a>Créer un programme

Nous allons aller plus loin en créant un nouveau programme simple.

1. Ouvrez Visual Studio. Dans le menu, choisissez **Fichier** > **Nouveau** > **Projet**.

  ![Fichier > Nouveau projet sur la barre de menus](../ide/media/VSIDE_Tour_NewProject1.png)

1. La boîte de dialogue **Nouveau projet** affiche plusieurs *modèles* de projet. Un modèle contient les fichiers et les paramètres de base nécessaires pour un type de projet donné. Choisissez la catégorie **.NET Core** sous **Visual C#**, puis choisissez le modèle **App. de console (.NET Core)**. Dans la zone de texte **Nom**, tapez **HelloWorld**, puis cliquez sur le bouton **OK**.

  ![Modèle d’application .NET Core](../ide/media/overview-new-project-dialog.png)

   Visual Studio crée le projet. Il s’agit d’une application « Hello world » simple, qui appelle la méthode <xref:System.Console.WriteLine?displayProperty=nameWithType> pour afficher la chaîne littérale « Hello World! » dans la fenêtre de console.

  > [!NOTE]
  > Si vous la catégorie **. NET Core** ne s’affiche pas, vous devez installer la charge de travail **Développement multiplateforme .NET Core**. Pour cela, cliquez sur le lien **Ouvrir Visual Studio Installer** en bas à gauche de la boîte de dialogue **Nouveau projet**. Une fois **Visual Studio Installer** ouvert, faites défiler l’écran vers le bas pour sélectionner la charge de travail **Développement multiplateforme .NET Core**, puis sélectionnez **Modifier**.

   Quelque chose qui ressemble à ce qui suit doit s’afficher :

   ![Environnement IDE de Visual Studio](../ide/media/overview-ide-console-app.png)

   Le code c# pour votre application est indiqué dans la fenêtre d’éditeur, ce qui occupe la majeure partie de l’espace. Notez que le texte est automatiquement colorisé pour indiquer les différents aspects du code, comme des mots clés et des types. En outre, les petites lignes en pointillés verticales du code indiquent les accolades correspondant entre elles et les numéros de ligne vous aident à localiser le code. Vous pouvez cliquer sur les signes moins encadrés pour réduire ou développer le code. Cette fonctionnalité de surlignage de code vous permet de masquer le code dont vous n’avez pas besoin, ce qui contribue à réduire l’encombrement à l’écran.

   Vos fichiers projet sont répertoriés sur le côté droit dans une fenêtre appelée **Explorateur de solutions**.

  ![IDE de Visual Studio avec zones rouges](../ide/media/overview-ide-console-app-red-boxes.png)

  Il existe d’autres menus et fenêtres d’outil, que nous aborderons par la suite.

1. Maintenant, démarrez l’application. Pour ce faire, vous pouvez choisir **Démarrer sans débogage** dans le menu **Déboguer** de la barre de menus. Vous pouvez également appuyer sur **Ctrl**+**F5**.

  ![Menu Déboguer > Démarrer sans débogage](../ide/media/overview-start-without-debugging.png)

  Visual Studio génère l’application, et une fenêtre de console s’ouvre avec le message **Hello World!**. Maintenant, votre application fonctionne !

  ![Fenêtre de console](../ide/media/overview-console-window.png)

1. Appuyez sur une touche au hasard pour fermer la fenêtre de console.

1. Ajoutons du code supplémentaire à l’application. Ajoutez le code C# suivant avant la ligne qui indique `Console.WriteLine("Hello World!");` :

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Ce code affiche **What is your name?** dans la fenêtre de console, puis attend que l’utilisateur entre du texte suivi de la touche **Entrée**.

1. Remplacez la ligne qui indique `Console.WriteLine("Hello World!");` par le code suivant :

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

1. Réexécutez l’application en sélectionnant **Déboguer** > **Démarrer sans débogage** ou en appuyant sur **Ctrl**+**F5**.

   Visual Studio régénère l’application et une fenêtre de console s’ouvre et vous demande votre nom.

1. Entrez votre nom dans la fenêtre de console et appuyez sur **Entrée**.

   ![Entrée de la fenêtre de console](media/overview-console-input.png)

1. Appuyez sur une touche pour fermer la fenêtre de console et arrêter le programme en cours d’exécution.

## <a name="use-refactoring-and-intellisense"></a>Utiliser la refactorisation et IntelliSense

Examinons comment la [refactorisation](refactoring-in-visual-studio.md) et [IntelliSense](using-intellisense.md) peuvent vous aider à coder plus efficacement au travers de deux ou trois exemples.

Tout d’abord, renommons la variable `name` :

1. Double-cliquez sur la variable `name` pour la sélectionner.

1. Tapez le nouveau nom de la variable, `username`.

   Notez qu’une zone grisée apparaît autour de la variable et qu’une ampoule s’affiche dans la marge.

1. Sélectionnez l’icône d’ampoule pour afficher les [Actions rapides](quick-actions.md) disponibles. Sélectionnez **Renommer « name » en « username »**.

   ![Renommer une action dans Visual Studio](media/rename-quick-action.png)

   La variable est renommée dans tout le projet, ce qui, dans notre cas, représente uniquement deux emplacements.

   ![Image GIF animée montrant la refactorisation du renommage dans Visual Studio](media/rename-refactoring.gif)

1. À présent, examinons IntelliSense. Tapez **DateTime now = DateTime.** sous la ligne qui indique `Console.WriteLine($"\nHello {username}!");`.

   Une zone affiche les membres de la classe <xref:System.DateTime>. De plus, la description du membre actuellement sélectionné s’affiche dans une zone distincte.

   ![Liste des membres IntelliSense dans Visual Studio](media/intellisense-list-members.png)

1. Sélectionnez le membre nommé **Now**, qui est une propriété de la classe, en double-cliquant dessus ou en appuyant sur **Tab**. Complétez la ligne de code en ajoutant un point-virgule (**;**).

1. Au-dessous, tapez ou copiez les lignes de code suivantes :

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > La méthode <xref:System.Console.Write%2A?displayProperty=nameWithType> est un peu différente de <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> dans la mesure où elle n’ajoute pas de marque de fin de ligne une fois imprimée. Cela signifie que la portion de texte suivante qui est envoyée à la sortie s’imprime sur la même ligne. Vous pouvez pointer sur chacune de ces méthodes dans votre code pour voir sa description.

1. Nous allons ensuite utiliser la refactorisation pour rendre le code un peu plus concis. Cliquez sur la variable `now` dans la ligne `DateTime now = DateTime.Now;`.

   Notez qu’une petite icône de tournevis apparaît dans la marge de cette ligne.

1. Cliquez sur l’icône de tournevis pour voir les suggestions disponibles dans Visual Studio. Dans le cas présent, il affiche la refactorisation de la [variable temporaire inline](reference/inline-temporary-variable.md) pour supprimer une ligne de code sans changer le comportement global :

   ![Refactorisation de la variable temporaire inline dans Visual Studio](media/inline-temporary-variable-refactoring.png)

1. Cliquez sur **Variable temporaire Inline** pour refactoriser le code.

1. Réexécutez le programme en appuyant sur **CTRL**+**F5**. La sortie ressemble à ceci :

   ![Fenêtre de console avec la sortie du programme](../ide/media/overview-console-final.png)

## <a name="debug-code"></a>Déboguer du code

Quand vous écrivez du code, vous devez l’exécuter et le tester pour rechercher les bogues. Le système de débogage de Visual Studio vous permet de parcourir le code instruction par instruction et d’en examiner les variables au fur et à mesure de votre avancement. Vous pouvez définir des points d’arrêt qui sont atteints seulement quand une condition spécifiée a la valeur true. Vous pouvez surveiller les valeurs des variables à mesure que le code s’exécute.

Définissons un point d’arrêt pour voir la valeur de la variable `username` quand le programme est en cours.

1. Recherchez la ligne de code qui indique `Console.WriteLine($"\nHello {username}!");`. Pour définir un point d’arrêt sur cette ligne de code, autrement dit, pour que l’exécution du programme soit suspendue au niveau de cette ligne, cliquez dans la bordure à l’extrême gauche de l’éditeur. Vous pouvez également cliquer n’importe où sur la ligne de code, puis appuyer sur **F9**.

   Un cercle rouge apparaît dans la bordure à gauche, et le code est surligné en rouge.

   ![Point d’arrêt sur une ligne de code dans Visual Studio](media/breakpoint.png)

1. Démarrez le débogage en sélectionnant **Déboguer** > **Démarrer le débogage** ou en appuyant sur **F5**.

1. Quand la fenêtre de console apparaît et vous demande votre nom, tapez-le, puis appuyez sur **Entrée**.

   Notez que le focus retourne à l’éditeur de code Visual Studio et que la ligne de code avec le point d’arrêt est surlignée en jaune. Cela signifie qu’il s’agit de la ligne de code suivante que le programme exécute.

1. Placez le pointeur de la souris sur la variable `username` pour afficher sa valeur. Vous pouvez également cliquer avec le bouton droit sur `username`, puis sélectionner **Ajouter un espion** pour ajouter la variable à la fenêtre **Espion**, dans laquelle vous pouvez également voir sa valeur.

   ![Valeur de la variable pendant le débogage dans Visual Studio](media/debugging-variable-value.png)

1. Pour laisser le programme s’exécuter jusqu’à son terme, appuyez à nouveau sur **F5**.

Pour en savoir plus sur le processus de débogage de Visual Studio, consultez [Visite guidée des fonctionnalités de débogage](../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Personnaliser Visual Studio

Vous pouvez personnaliser l’IDE, notamment en changeant le thème de couleur par défaut. Pour remplacer le thème par **Sombre** :

1. Dans la barre de menus, choisissez **Outils** > **Options** pour ouvrir la boîte de dialogue **Options**.

1. Dans la page **Environnement** > **Options générales**, remplacez la sélection du **Thème de couleur** par **Sombre**, puis choisissez **OK**.

   Le thème de couleur de l’ensemble de l’IDE devient **Sombre**.

   ![VS en thème Sombre](media/quickstart-personalize-dark-theme.png)

Pour en savoir plus sur les autres façons possibles de personnaliser l’IDE, consultez [Personnaliser Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="learn-more"></a>En savoir plus

Voulez-vous créer une application pour un téléphone Android ou iOS ? Qu’en est-il d’un jeu 3D ou d’une application cloud ? Pour en savoir plus sur ces fonctionnalités de Visual Studio et sur d’autres, consultez [Fonctionnalités de Visual Studio 2017](../ide/advanced-feature-overview.md).

Si vous êtes prêt à commencer à coder maintenant, choisissez l’une des rubriques de démarrage rapide dans la table des matières, comme [Créer votre première application web ASP.NET Core](quickstart-aspnet-core.md).

Vous pouvez également consulter les cours Visual Studio gratuits disponibles sur [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033).

## <a name="see-also"></a>Voir aussi

* [Autres fonctionnalités de Visual Studio](../ide/advanced-feature-overview.md)
* [www.visualstudio.com](https://www.visualstudio.com/vs/)
* [Le blog Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/)
* [Téléchargements Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)