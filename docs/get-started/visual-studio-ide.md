---
title: Vue d’ensemble de Visual Studio 2017
titleSuffix: ''
ms.date: 10/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
ms.custom: vs-get-started
author: gewarren
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- MSDNSTART
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fad0568804c4cd455a195c476cd2cd447ef5827f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954772"
---
# <a name="welcome-to-the-visual-studio-ide"></a>Bienvenue dans l’IDE Visual Studio

*L’environnement de développement intégré* de Visual Studio est une plateforme de lancement créative avec laquelle vous pouvez modifier, déboguer et générer du code, puis publier une application. Un environnement de développement intégré (IDE) est un programme riche en fonctionnalités qui peut être utilisé pour de nombreux aspects du développement de logiciels. Au-delà de l’éditeur et du débogueur standard fournis par la plupart des IDE, Visual Studio inclut des compilateurs, des outils de complétion de code, des concepteurs graphiques et de nombreuses autres fonctionnalités afin de faciliter le processus de développement logiciel.

![IDE de Visual Studio](media/visual-studio-ide.png)

Cette image montre Visual Studio avec un projet ouvert et plusieurs fenêtres Outil principales dont vous êtes susceptible de vous servir :

- L’[**Explorateur de solutions**](../ide/solutions-and-projects-in-visual-studio.md) (en haut à droite) vous permet d’afficher, de parcourir et de gérer vos fichiers de code. L’**Explorateur de solutions** peut vous aider à organiser votre code en regroupant les fichiers dans des [projets et des solutions](../get-started/tutorial-projects-solutions.md).

- La [fenêtre de l’éditeur](../ide/writing-code-in-the-code-and-text-editor.md) (au centre), où vous passerez sans doute la plupart de votre temps, affiche le contenu des fichiers. C’est là que vous pouvez modifier le code ou concevoir une interface utilisateur telle qu’une fenêtre avec des boutons et des zones de texte.

- La [fenêtre Sortie](../ide/reference/output-window.md) (en bas au centre) est l’emplacement où Visual Studio envoie des notifications telles que les messages d’erreur et de débogage, les avertissements du compilateur, les messages d’état de publication, entre autres. Chaque source de message a son propre onglet.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (en bas à droite) vous permet de suivre des éléments de travail et de partager du code avec d’autres utilisateurs à l’aide des technologies de gestion de versions comme [Git](https://git-scm.com/) et [Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Éditions

Visual Studio est disponible pour Windows et Mac. [Visual Studio pour Mac](/visualstudio/mac/) compte de nombreuses fonctionnalités en commun avec Visual Studio 2017, et est optimisé pour le développement d’applications mobiles et multiplateformes. Cet article traite essentiellement de la version Windows de Visual Studio 2017.

Il existe trois éditions de Visual Studio 2017 : Community, Professional et Enterprise. Consultez [Comparez les IDE Visual Studio 2017](https://visualstudio.microsoft.com/vs/compare/) pour en savoir plus sur les fonctionnalités prises en charge dans chaque édition.

## <a name="popular-productivity-features"></a>Fonctionnalités de productivité populaires

Voici quelques-unes des fonctionnalités populaires de Visual Studio qui vous aident à être plus productifs quand vous développez des logiciels :

- [Refactorisation](../ide/refactoring-in-visual-studio.md)

   La refactorisation inclut des opérations telles que le renommage intelligent des variables, l’extraction d’une ou plusieurs lignes de code dans une nouvelle méthode, le changement de l’ordre des paramètres de méthode, et bien plus encore.

   ![Refactorisation dans Visual Studio](media/refactoring-menu.png)

- [IntelliSense](../ide/using-intellisense.md)

   IntelliSense est un terme désignant un ensemble de fonctionnalités qui affichent des informations relatives au code directement dans l’éditeur et qui, dans certains cas, écrivent de petits bouts de code à votre place. Cela revient à avoir de la documentation de base incluse dans l’éditeur, ce qui vous évite d’avoir à rechercher ailleurs des informations sur les types. Les fonctionnalités d'IntelliSense varient selon le langage. Pour plus d’informations, consultez [C# IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md) et [Visual Basic IntelliSense](../ide/visual-basic-specific-intellisense.md). L’illustration suivante montre comment IntelliSense affiche une liste des membres d’un type :

   ![Liste des membres Visual Studio](media/intellisense-list-members.png)

- [Lancement rapide](../ide/reference/quick-launch-environment-options-dialog-box.md)

   La maîtrise de Visual Studio peut sembler insurmontable parfois, avec autant de menus, d’options et de propriétés. La zone de recherche **Lancement rapide** est un excellent moyen de trouver rapidement ce dont vous avez besoin dans Visual Studio. Quand vous commencez à taper le nom d’un élément que vous recherchez, Visual Studio affiche des résultats qui vous mènent exactement où vous devez accéder. Si vous avez besoin ajouter des fonctionnalités à Visual Studio, par exemple pour ajouter la prise en charge d’un langage de programmation supplémentaire, **Lancement rapide** fournit des résultats qui ouvrent Visual Studio Installer pour installer une charge de travail ou un composant spécifique.

   ![Zone de recherche Lancement rapide dans Visual Studio](media/quick-launch-nuget.png)

- Tildes et [Actions rapides](../ide/quick-actions.md)

   Les tildes sont des soulignements ondulés qui vous signalent des erreurs ou des problèmes potentiels dans votre code en cours de frappe. Ces indices visuels permettent de résoudre les problèmes immédiatement sans attendre que l’erreur soit découverte durant la génération ou quand vous exécutez le programme. Si vous pointez sur un tilde, vous voyez des informations supplémentaires sur l’erreur. Une ampoule (appelée Action rapide) peut également apparaître dans la marge gauche, avec des actions pour corriger l’erreur.

   ![Tildes dans Visual Studio](media/squiggles-error.png)

- [Hiérarchie d’appels](../ide/reference/call-hierarchy.md)

   La fenêtre **Hiérarchie d’appels** affiche les méthodes qui appellent une méthode sélectionnée. Ces informations peuvent être utiles quand vous envisagez de changer ou de supprimer la méthode, ou quand vous essayez de repérer un bogue.

   ![Fenêtre Hiérarchie d'appels](../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens vous aide à rechercher les références à votre code, les modifications apportées à votre code, les bogues liés, les éléments de travail, les revues de code et les tests unitaires, tout cela sans quitter l’éditeur.

   ![CodeLens](media/codelens-overview.png)

- [Atteindre la définition](../ide/go-to-and-peek-definition.md)

   La fonctionnalité Atteindre la définition vous mène directement à l’emplacement où une fonction ou un type est défini(e).

   ![Atteindre la définition](media/go-to-definition-menu.png)

- [Aperçu de définition](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   La fenêtre **Aperçu de définition** montre la définition d’une méthode ou d’un type sans réellement ouvrir un fichier distinct.

   ![Aperçu de définition](media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Installer l’IDE de Visual Studio

Cet article de vue d’ensemble vous montre comment créer un projet simple et essayer certaines opérations réalisables avec Visual Studio, telles que la modification du thème de couleur, l’utilisation d’[IntelliSense](../ide/using-intellisense.md) comme aide au codage et le débogage d’une application pour afficher la valeur d’une variable pendant l’exécution du programme. Pour commencer, [téléchargez Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) et installez-le sur votre système.

Le programme d’installation modulaire vous permet de choisir et d’installer des *charges de travail*, qui sont des groupes de fonctionnalités requises pour la plateforme ou le langage de programmation de votre choix. Pour suivre les étapes de [création d’un programme](#create-a-program), veillez à sélectionner la charge de travail **Développement multiplateforme .NET Core** pendant l’installation.

![Charge de travail Développement multiplateforme .NET Core dans Visual Studio Installer](media/dotnet-core-cross-platform-workload.png)

Quand vous démarrez Visual Studio pour la première fois, vous pouvez vous [connecter](../ide/signing-in-to-visual-studio.md) avec votre compte Microsoft, ou avec votre compte professionnel ou scolaire.

## <a name="create-a-program"></a>Créer un programme

Nous allons aller plus loin en créant un programme simple.

1. Ouvrez Visual Studio. Dans le menu, choisissez **Fichier** > **Nouveau** > **Projet**.

   ![Fichier > Nouveau projet sur la barre de menus](media/file-new-project-menu.png)

2. La boîte de dialogue **Nouveau projet** affiche plusieurs *modèles* de projet. Un modèle contient les fichiers et les paramètres de base nécessaires pour un type de projet donné. Choisissez la catégorie **.NET Core** sous **Visual C#**, puis choisissez le modèle **App. de console (.NET Core)**. Dans la zone de texte **Nom**, tapez **HelloWorld**, puis cliquez sur le bouton **OK**.

   ![Modèle d’application .NET Core](media/overview-new-project-dialog.png)

   Visual Studio crée le projet. Il s’agit d’une application « Hello world » simple, qui appelle la méthode <xref:System.Console.WriteLine?displayProperty=nameWithType> pour afficher la chaîne littérale « Hello World! » dans la fenêtre de console (sortie du programme).

   > [!NOTE]
   > Si vous la catégorie **. NET Core** ne s’affiche pas, vous devez installer la charge de travail **Développement multiplateforme .NET Core**. Pour cela, cliquez sur le lien **Ouvrir Visual Studio Installer** en bas à gauche de la boîte de dialogue **Nouveau projet**. Une fois Visual Studio Installer ouvert, faites défiler l’écran vers le bas pour sélectionner la charge de travail **Développement multiplateforme .NET Core**, puis sélectionnez **Modifier**.

   Quelque chose qui ressemble à ce qui suit doit s’afficher :

   ![Environnement IDE de Visual Studio](media/overview-ide-console-app.png)

   Le code C# de votre application figure dans la fenêtre d’éditeur, qui occupe la majeure partie de l’espace. Notez que le texte est colorisé automatiquement pour indiquer les différentes parties du code, comme les mots clés et les types. En outre, les petites lignes en pointillés verticales du code indiquent les accolades correspondant entre elles et les numéros de ligne vous aident à localiser le code. Vous pouvez cliquer sur les signes moins encadrés pour réduire ou développer des blocs de code. Cette fonctionnalité de surlignage de code vous permet de masquer le code dont vous n’avez pas besoin, ce qui contribue à réduire l’encombrement à l’écran. Vos fichiers projet sont répertoriés sur le côté droit dans une fenêtre appelée **Explorateur de solutions**.

   ![IDE de Visual Studio avec zones rouges](media/overview-ide-console-app-red-boxes.png)

   Il existe d’autres menus et fenêtres d’outil, que nous aborderons par la suite.

3. Maintenant, démarrez l’application. Pour ce faire, vous pouvez choisir **Démarrer sans débogage** dans le menu **Déboguer** de la barre de menus. Vous pouvez également appuyer sur **Ctrl**+**F5**.

   ![Menu Déboguer > Démarrer sans débogage](media/overview-start-without-debugging.png)

   Visual Studio génère l’application, et une fenêtre de console s’ouvre avec le message **Hello World!**. Maintenant, votre application fonctionne !

   ![Fenêtre de console](media/overview-console-window.png)

4. Appuyez sur une touche au hasard pour fermer la fenêtre de console.

5. Ajoutons du code supplémentaire à l’application. Ajoutez le code C# suivant avant la ligne qui indique `Console.WriteLine("Hello World!");` :

   ```csharp
   Console.WriteLine("\nWhat is your name?");
   var name = Console.ReadLine();
   ```

   Ce code affiche **What is your name?** dans la fenêtre de console, puis attend que l’utilisateur entre du texte suivi de la touche **Entrée**.

6. Remplacez la ligne qui indique `Console.WriteLine("Hello World!");` par le code suivant :

   ```csharp
   Console.WriteLine($"\nHello {name}!");
   ```

7. Réexécutez l’application en sélectionnant **Déboguer** > **Démarrer sans débogage** ou en appuyant sur **Ctrl**+**F5**.

   Visual Studio régénère l’application et une fenêtre de console s’ouvre et vous demande votre nom.

8. Entrez votre nom dans la fenêtre de console et appuyez sur **Entrée**.

   ![Entrée de la fenêtre de console](media/overview-console-input.png)

9. Appuyez sur une touche pour fermer la fenêtre de console et arrêter le programme en cours d’exécution.

## <a name="use-refactoring-and-intellisense"></a>Utiliser la refactorisation et IntelliSense

Examinons comment la [refactorisation](../ide/refactoring-in-visual-studio.md) et [IntelliSense](../ide/using-intellisense.md) peuvent vous aider à coder plus efficacement au travers de deux ou trois exemples.

Tout d’abord, renommons la variable `name` :

1. Double-cliquez sur la variable `name` pour la sélectionner.

2. Tapez le nouveau nom de la variable, **username**.

   Notez qu’une zone grisée apparaît autour de la variable et qu’une ampoule s’affiche dans la marge.

3. Sélectionnez l’icône d’ampoule pour afficher les [Actions rapides](../ide/quick-actions.md) disponibles. Sélectionnez **Renommer « name » en « username »**.

   ![Renommer une action dans Visual Studio](media/rename-quick-action.png)

   La variable est renommée dans tout le projet, ce qui, dans notre cas, représente uniquement deux emplacements.

   ![Image GIF animée montrant la refactorisation du renommage dans Visual Studio](media/rename-refactoring.gif)

4. À présent, examinons IntelliSense. Tapez **DateTime now = DateTime.** sous la ligne qui indique `Console.WriteLine($"\nHello {username}!");`.

   Une zone affiche les membres de la classe <xref:System.DateTime>. De plus, la description du membre actuellement sélectionné s’affiche dans une zone distincte.

   ![Liste des membres IntelliSense dans Visual Studio](media/intellisense-list-members.png)

5. Sélectionnez le membre nommé **Now**, qui est une propriété de la classe, en double-cliquant dessus ou en appuyant sur **Tab**. Complétez la ligne de code en ajoutant un point-virgule (**;**).

6. Au-dessous, tapez ou copiez les lignes de code suivantes :

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > La méthode <xref:System.Console.Write%2A?displayProperty=nameWithType> est un peu différente de <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> dans la mesure où elle n’ajoute pas de marque de fin de ligne une fois imprimée. Cela signifie que la portion de texte suivante qui est envoyée à la sortie s’imprime sur la même ligne. Vous pouvez pointer sur chacune de ces méthodes dans votre code pour voir sa description.

7. Nous allons ensuite utiliser la refactorisation pour rendre le code un peu plus concis. Cliquez sur la variable `now` dans la ligne `DateTime now = DateTime.Now;`.

   Notez qu’une petite icône de tournevis apparaît dans la marge de cette ligne.

8. Cliquez sur l’icône de tournevis pour voir les suggestions disponibles dans Visual Studio. Dans le cas présent, il affiche la refactorisation de la [variable temporaire inline](../ide/reference/inline-temporary-variable.md) pour supprimer une ligne de code sans changer le comportement global :

   ![Refactorisation de la variable temporaire inline dans Visual Studio](media/inline-temporary-variable-refactoring.png)

9. Cliquez sur **Variable temporaire Inline** pour refactoriser le code.

10. Réexécutez le programme en appuyant sur **CTRL**+**F5**. La sortie ressemble à ceci :

   ![Fenêtre de console avec la sortie du programme](media/overview-console-final.png)

## <a name="debug-code"></a>Déboguer du code

Quand vous écrivez du code, vous devez l’exécuter et le tester pour rechercher les bogues. Le système de débogage de Visual Studio vous permet de parcourir le code instruction par instruction et d’en examiner les variables au fur et à mesure de votre avancement. Vous pouvez définir des *points d’arrêt* qui arrêtent l’exécution du code à une ligne particulière. Vous pouvez observer la façon dont la valeur d’une variable change à mesure que le code s’exécute, et bien plus encore.

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

Vous pouvez personnaliser l’interface utilisateur de Visual Studio, notamment changer le thème de couleur par défaut. Pour remplacer le thème par **Sombre** :

1. Dans la barre de menus, choisissez **Outils** > **Options** pour ouvrir la boîte de dialogue **Options**.

2. Dans la page **Environnement** > **Options générales**, remplacez la sélection du **Thème de couleur** par **Sombre**, puis choisissez **OK**.

   Le thème de couleur de l’ensemble de l’IDE devient **Sombre**.

   ![Visual Studio en thème sombre](media/dark-theme.png)

Pour en savoir plus sur les autres façons possibles de personnaliser l’IDE, consultez [Personnaliser Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="next-steps"></a>Étapes suivantes

Explorez davantage Visual Studio en suivant l’un de ces articles d’introduction :

- Familiarisez-vous avec l’éditeur de code dans [Apprendre à utiliser l’éditeur de code](../get-started/tutorial-editor.md)

- Découvrez comment Visual Studio organise le code dans [Découvrir les projets et les solutions](../get-started/tutorial-projects-solutions.md)

Si vous êtes prêt à aller plus loin dans le codage, l’un des guides de démarrage rapide spécifiques au langage est une bonne prochaine étape :

- [Utiliser Visual Studio pour créer votre première application web Python](../ide/quickstart-python.md)

- [Utiliser Visual Studio pour créer votre première application web C#](../ide/quickstart-aspnet-core.md)

- [Utiliser Visual Studio pour créer votre première application web F#](../ide/quickstart-fsharp.md)

- [Utiliser Visual Studio pour créer votre première application Node.js](../ide/quickstart-nodejs.md)

- [Bien démarrer avec C++ dans Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md)

## <a name="see-also"></a>Voir aussi

- Découvrir d’[autres fonctionnalités de Visual Studio](../ide/advanced-feature-overview.md)
- Visiter [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Lire le [blog Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/)
- Accéder aux cours Visual Studio gratuits sur [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033)
- Télécharger Visual Studio sur [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
