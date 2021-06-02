---
ms.date: 05/28/2021
ms.technology: vs-ide-general
ms.custom: vs-get-started
ms.author: tglee
author: TerryGLee
manager: jmartens
ms.topic: include
ms.openlocfilehash: 3c5cb8d78b254c667ecd131ef3850475a0460323
ms.sourcegitcommit: 5366c6bca3fb217a2fbf847998387578f51ec45c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2021
ms.locfileid: "110748526"
---
*L’environnement de développement intégré* de Visual Studio est une plateforme de lancement créative avec laquelle vous pouvez modifier, déboguer et générer du code, puis publier une application. Un environnement de développement intégré (IDE) est un programme riche en fonctionnalités qui peut être utilisé pour de nombreux aspects du développement de logiciels. Au-delà de l’éditeur et du débogueur standard fournis par la plupart des IDE, Visual Studio inclut des compilateurs, des outils de complétion de code, des concepteurs graphiques et de nombreuses autres fonctionnalités afin de faciliter le processus de développement logiciel.

::: moniker range="vs-2017"

![IDE de Visual Studio 2017](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range="vs-2019"

:::image type="content" source="../media/vs-2019/ide-overview.png" alt-text="Capture d’écran de l’IDE de Visual Studio, qui comprend des légendes qui indiquent où se trouvent les fonctionnalités et fonctionnalités clés." lightbox="../media/vs-2019/ide-overview.png":::

::: moniker-end

Cette image montre Visual Studio avec un projet ouvert et plusieurs fenêtres Outil principales dont vous êtes susceptible de vous servir :

- L’[Explorateur de solutions](../../ide/solutions-and-projects-in-visual-studio.md) (en haut à droite) vous permet d’afficher, de parcourir et de gérer vos fichiers de code. **Explorateur de solutions** pouvez vous aider à organiser votre code en regroupant les fichiers dans des [solutions et des projets](../tutorial-projects-solutions.md).

- La [fenêtre de l’éditeur](../../ide/writing-code-in-the-code-and-text-editor.md) (au centre), où vous passerez sans doute la plupart de votre temps, affiche le contenu des fichiers. C’est là que vous pouvez modifier le code ou concevoir une interface utilisateur telle qu’une fenêtre avec des boutons et des zones de texte.

::: moniker range="vs-2017"

- La [fenêtre Sortie](../../ide/reference/output-window.md) (en bas au centre) est l’emplacement où Visual Studio envoie des notifications telles que les messages d’erreur et de débogage, les avertissements du compilateur, les messages d’état de publication, entre autres. Chaque source de message a son propre onglet.

::: moniker-end

- [Les modifications git](/visualstudio/version-control/) (en bas à droite) vous permettent d’effectuer le suivi des éléments de travail et de partager du code avec d’autres personnes à l’aide de technologies de contrôle de version telles que [git](https://git-scm.com/) et [GitHub](https://docs.github.com/github).

## <a name="editions"></a>Éditions

::: moniker range="vs-2017"

Visual Studio est disponible pour Windows et Mac. [Visual Studio pour Mac](/visualstudio/mac/) compte de nombreuses fonctionnalités en commun avec Visual Studio 2017, et est optimisé pour le développement d’applications mobiles et multiplateformes. Cet article traite essentiellement de la version Windows de Visual Studio 2017.

Il existe trois éditions de Visual Studio : Community, Professional et Enterprise. Consultez [comparer les éditions de Visual Studio](https://visualstudio.microsoft.com/vs/compare/) pour en savoir plus sur les fonctionnalités prises en charge dans chaque édition.

::: moniker-end

::: moniker range="vs-2019"

Visual Studio est disponible pour Windows et Mac. [Visual Studio pour Mac](/visualstudio/mac/) compte de nombreuses fonctionnalités en commun avec Visual Studio 2019, et est optimisé pour le développement d’applications mobiles et multiplateformes. Cet article traite essentiellement de la version Windows de Visual Studio 2019.

Il existe trois éditions de Visual Studio 2019 : Community, Professional et Enterprise. Consultez [comparer les éditions de Visual Studio](https://visualstudio.microsoft.com/vs/compare/) pour en savoir plus sur les fonctionnalités prises en charge dans chaque édition.

::: moniker-end

## <a name="popular-productivity-features"></a>Fonctionnalités de productivité populaires

Voici quelques-unes des fonctionnalités populaires de Visual Studio qui vous aident à être plus productifs quand vous développez des logiciels :

- Tildes et [Actions rapides](../../ide/quick-actions.md)

   Les tildes sont des soulignements ondulés qui vous signalent des erreurs ou des problèmes potentiels dans votre code en cours de frappe. Ces indices visuels permettent de résoudre les problèmes immédiatement sans attendre que l’erreur soit découverte durant la génération ou quand vous exécutez le programme. Si vous pointez sur un tilde, vous voyez des informations supplémentaires sur l’erreur. Une ampoule (appelée Action rapide) peut également apparaître dans la marge gauche, avec des actions pour corriger l’erreur.

   ![Tildes dans Visual Studio](../media/squiggles-error.png)

::: moniker range=">=vs-2019"

- Nettoyage du code

   D’un seul clic sur un bouton, formatez votre code et appliquez des correctifs de code suggérés par votre [paramètres de style de code](../../ide/reference/options-text-editor-csharp-formatting.md), [conventions .editorconfig](../../ide/create-portable-custom-editor-options.md) et [analyseurs Roslyn](../../code-quality/roslyn-analyzers-overview.md). Le **nettoyage du code** vous permet de résoudre des problèmes dans votre code avant de passer à la révision du code. (Actuellement disponible pour le code C# uniquement.)

   ![Bouton de nettoyage du code dans Visual Studio](../media/vs-2019/code-cleanup.png)

::: moniker-end

- [Refactorisation](../../ide/refactoring-in-visual-studio.md)

   La refactorisation inclut des opérations telles que le renommage intelligent des variables, l’extraction d’une ou plusieurs lignes de code dans une nouvelle méthode, le changement de l’ordre des paramètres de méthode, et bien plus encore.

   ![Refactorisation dans Visual Studio](../media/refactoring-menu.png)

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense est un terme désignant un ensemble de fonctionnalités qui affichent des informations relatives au code directement dans l’éditeur et qui, dans certains cas, écrivent de petits bouts de code à votre place. Cela revient à avoir de la documentation de base incluse dans l’éditeur, ce qui vous évite d’avoir à rechercher ailleurs des informations sur les types. Les fonctionnalités d'IntelliSense varient selon le langage. Pour plus d’informations, consultez [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md) et [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). L’illustration suivante montre comment IntelliSense affiche une liste des membres d’un type :

   ![Liste des membres Visual Studio](../media/intellisense-list-members.png)

- [Recherche Visual Studio](../../ide/visual-studio-search.md)

   La maîtrise de Visual Studio peut sembler insurmontable parfois, avec autant de menus, d’options et de propriétés. La recherche Visual Studio (**CTRL** + **Q**) est un excellent moyen de trouver rapidement les fonctionnalités et le code de l’IDE à un seul endroit.

   ::: moniker range="vs-2017"

   ![Zone de recherche Lancement rapide dans Visual Studio 2017](../media/quick-launch-nuget.png)

   Pour plus d’informations, consultez [Lancement rapide](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Zone de recherche dans Visual Studio 2019](../media/vs-2019/quick-launch-nuget.png)

    Pour plus d’informations et de conseils sur la productivité, consultez [comment utiliser la recherche Visual Studio](../../ide/visual-studio-search.md).

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Modifiez et déboguez de manière collaborative avec d’autres utilisateurs en temps réel, quel que soit le type de votre application ou le langage de programmation. Vous pouvez partager instantanément et en toute sécurité votre projet puis partager au besoin des sessions de débogage, des instances de terminal, des applications web localhost, des appels vocaux, etc.

- [Hiérarchie d'appels](../../ide/reference/call-hierarchy.md)

   La fenêtre **Hiérarchie d’appels** affiche les méthodes qui appellent une méthode sélectionnée. Ces informations peuvent être utiles quand vous envisagez de changer ou de supprimer la méthode, ou quand vous essayez de repérer un bogue.

   ![Fenêtre Hiérarchie d'appels](../../ide/reference/media/call-hierarchy-csharp-expanded.png)

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens vous aide à rechercher les références à votre code, les modifications apportées à votre code, les bogues liés, les éléments de travail, les revues de code et les tests unitaires, tout cela sans quitter l’éditeur.

   ![CodeLens](../media/codelens-overview.png)

- [Atteindre la définition](../../ide/go-to-and-peek-definition.md)

   La fonctionnalité Atteindre la définition vous mène directement à l’emplacement où une fonction ou un type est défini(e).

   ![Atteindre la définition](../media/go-to-definition-menu.png)

- [Aperçu de définition](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   La fenêtre **Aperçu de définition** montre la définition d’une méthode ou d’un type sans réellement ouvrir un fichier distinct.

   ![Aperçu de définition](../media/peek-definition.png)

## <a name="install-the-visual-studio-ide"></a>Installer l’IDE de Visual Studio

Dans cette section, vous allez créer un projet simple afin d’essayer des actions que vous pouvez réaliser avec Visual Studio. Vous allez utiliser [IntelliSense](../../ide/using-intellisense.md) comme aide au codage, déboguer une application pour afficher la valeur d’une variable pendant l’exécution du programme et modifier le thème de couleur.

::: moniker range="vs-2017"

Pour commencer, [téléchargez Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) et installez-le sur votre système. Le programme d’installation modulaire vous permet de choisir et d’installer des *charges de travail*, qui sont des groupes de fonctionnalités requises pour la plateforme ou le langage de programmation de votre choix. Pour suivre les étapes de [création d’un programme](#create-a-program), veillez à sélectionner la charge de travail **Développement multiplateforme .NET Core** pendant l’installation.

::: moniker-end

::: moniker range=">=vs-2019"

Pour commencer, [téléchargez Visual Studio](https://visualstudio.microsoft.com/downloads) et installez-le sur votre système. Le programme d’installation modulaire vous permet de choisir et d’installer des *charges de travail*, qui sont des groupes de fonctionnalités requises pour la plateforme ou le langage de programmation de votre choix. Pour suivre les étapes de [création d’un programme](#create-a-program), veillez à sélectionner la charge de travail **Développement multiplateforme .NET Core** pendant l’installation.

::: moniker-end

![Charge de travail Développement multiplateforme .NET Core dans Visual Studio Installer](../media/dotnet-core-cross-platform-workload.png)

Lorsque vous ouvrez Visual Studio pour la première fois, vous pouvez vous [connecter](../../ide/signing-in-to-visual-studio.md) avec votre compte Microsoft ou avec votre compte professionnel ou scolaire.

## <a name="create-a-program"></a>Créer un programme

Nous allons aller plus loin en créant un programme simple.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio.

1. Dans la barre de menus, choisissez **fichier** > **nouveau** > **projet**.

   ![Fichier > Nouveau projet sur la barre de menus](../media/file-new-project-menu.png)

   La boîte **de dialogue Nouveau projet** affiche plusieurs *modèles* de projet. Un modèle contient les fichiers et les paramètres de base nécessaires pour un type de projet donné.

1. Choisissez la catégorie de modèle **.NET Core** sous **Visual C#**, puis choisissez le modèle **Application console (.NET Core)**. Dans la zone de texte **Nom**, tapez **HelloWorld**, puis cliquez sur le bouton **OK**.

   ![Modèle d’application .NET Core](../media/overview-new-project-dialog.png)

   > [!NOTE]
   > Si vous la catégorie **. NET Core** ne s’affiche pas, vous devez installer la charge de travail **Développement multiplateforme .NET Core**. Pour cela, cliquez sur le lien **Ouvrir Visual Studio Installer** en bas à gauche de la boîte de dialogue **Nouveau projet**. Une fois Visual Studio Installer ouvert, faites défiler l’écran vers le bas pour sélectionner la charge de travail **Développement multiplateforme .NET Core**, puis sélectionnez **Modifier**.

   Visual Studio crée le projet. Il s’agit d’une application « Hello world » simple, qui appelle la méthode <xref:System.Console.WriteLine?displayProperty=nameWithType> pour afficher la chaîne littérale « Hello World! » dans la fenêtre de console (sortie du programme).

   Quelque chose qui ressemble à ce qui suit doit s’afficher :

   ![Environnement IDE de Visual Studio](../media/overview-ide-console-app.png)

   Le code C# de votre application figure dans la fenêtre d’éditeur, qui occupe la majeure partie de l’espace. Notez que le texte est colorisé automatiquement pour indiquer les différentes parties du code, comme les mots clés et les types. En outre, les petites lignes en pointillés verticales du code indiquent les accolades correspondant entre elles et les numéros de ligne vous aident à localiser le code. Vous pouvez cliquer sur les signes moins encadrés pour réduire ou développer des blocs de code. Cette fonctionnalité de surlignage de code vous permet de masquer le code dont vous n’avez pas besoin, ce qui contribue à réduire l’encombrement à l’écran. Vos fichiers projet sont répertoriés sur le côté droit dans une fenêtre appelée **Explorateur de solutions**.

   ![IDE de Visual Studio avec zones rouges](../media/overview-ide-console-app-red-boxes.png)

   Il existe d’autres menus et fenêtres d’outil, que nous aborderons par la suite.

1. Maintenant, démarrez l’application. Pour ce faire, vous pouvez choisir **Démarrer sans débogage** dans le menu **Déboguer** de la barre de menus. Vous pouvez également appuyer sur **CTRL** + **F5**.

   ![Menu Déboguer > Démarrer sans débogage](../media/overview-start-without-debugging.png)

   Visual Studio génère l’application, et une fenêtre de console s’ouvre avec le message **Hello World!**. Maintenant, votre application fonctionne !

   ![Capture d’écran de la fenêtre de console cmd.exe montrant la sortie’Hello Word ! ' et « appuyez sur une touche pour continuer ».](../media/overview-console-window.png)

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

1. Réexécutez l’application en sélectionnant **Déboguer** > **Démarrer sans débogage** ou en appuyant sur **CTRL** + **F5**.

   Visual Studio régénère l’application et une fenêtre de console s’ouvre et vous demande votre nom.

1. Entrez votre nom dans la fenêtre de console et appuyez sur **Entrée**.

   ![Entrée de la fenêtre de console](../media/overview-console-input.png)

1. Appuyez sur une touche pour fermer la fenêtre de console et arrêter le programme en cours d’exécution.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio.

   La fenêtre de démarrage s’affiche avec différentes options de clonage d’un référentiel, d’ouverture d’un projet récent ou de création d’un tout nouveau projet.

1. Choisissez **créer un nouveau projet**.

    :::image type="content" source="../media/vs-2019/start-window-create-new-project.png" alt-text="Capture d’écran de la fenêtre créer un nouveau projet dans Visual Studio 2019.":::

   La fenêtre **Créer un projet** s’affiche et présente plusieurs *modèles* de projet. Un modèle contient les fichiers et les paramètres de base requis pour un type de projet donné.

1. Pour rechercher le modèle souhaité, tapez ou entrez **console .net core** dans la zone de recherche. La liste des modèles disponibles est automatiquement filtrée en fonction des mots clés que vous avez entrés. Vous pouvez filtrer davantage les résultats du modèle en choisissant **C#** dans la liste déroulante **tous les langages** , **Windows** dans la liste **toutes les plateformes** et la **console** dans la liste tous les **types de projets** .

    Sélectionnez le modèle **application console** , puis cliquez sur **suivant**.

    :::image type="content" source="../media/vs-2019/create-new-project.png" alt-text="Capture d’écran de la fenêtre créer un nouveau projet dans Visual Studio 2019, où vous sélectionnez le modèle souhaité.":::

1. Dans la fenêtre **configurer votre nouveau projet** , entrez **HelloWorld** dans la zone **nom du projet** , modifiez éventuellement l’emplacement du répertoire pour vos fichiers projet (les paramètres régionaux par défaut sont `C:\Users\<name>\source\repos` ), puis cliquez sur **suivant**.

    :::image type="content" source="../media/vs-2019/configure-new-project.png" alt-text="Capture d’écran de la fenêtre « configurer votre nouveau projet » dans Visual Studio 2019, où vous entrez le nom du projet.":::

1. Dans la fenêtre **informations supplémentaires** , vérifiez que **.net Core 3,1** s’affiche dans le menu déroulant **Framework cible** , puis cliquez sur **créer**.

    :::image type="content" source="../media/vs-2019/create-project-additional-info.png" alt-text="Capture d’écran de la fenêtre « informations supplémentaires » dans Visual Studio 2019, où vous sélectionnez la version de .NET Core Framework que vous souhaitez.":::

   Visual Studio crée le projet. Il s’agit d’une application « Hello world » simple, qui appelle la méthode <xref:System.Console.WriteLine?displayProperty=nameWithType> pour afficher la chaîne littérale « Hello World! » dans la fenêtre de console (sortie du programme).

   Quelque chose qui ressemble à ce qui suit doit s’afficher :

   ![Environnement IDE de Visual Studio](../media/vs-2019/overview-ide-console-app.png)

   Le code C# de votre application figure dans la fenêtre d’éditeur, qui occupe la majeure partie de l’espace. Notez que le texte est colorisé automatiquement pour indiquer les différentes parties du code, comme les mots clés et les types. En outre, les petites lignes en pointillés verticales du code indiquent les accolades correspondant entre elles et les numéros de ligne vous aident à localiser le code. Vous pouvez cliquer sur les signes moins encadrés pour réduire ou développer des blocs de code. Cette fonctionnalité de surlignage de code vous permet de masquer le code dont vous n’avez pas besoin, ce qui contribue à réduire l’encombrement à l’écran. Vos fichiers projet sont répertoriés sur le côté droit dans une fenêtre appelée **Explorateur de solutions**.

   ![IDE de Visual Studio avec zones rouges](../media/vs-2019/overview-ide-console-app-red-boxes.png)

   Il existe d’autres menus et fenêtres d’outil, que nous aborderons par la suite.

1. Maintenant, démarrez l’application. Pour ce faire, vous pouvez choisir **Démarrer sans débogage** dans le menu **Déboguer** de la barre de menus. Vous pouvez également appuyer sur **CTRL** + **F5**.

   ![Menu Déboguer > Démarrer sans débogage](../media/overview-start-without-debugging.png)

   Visual Studio génère l’application, et une fenêtre de console s’ouvre avec le message **Hello World!**. Maintenant, votre application fonctionne !

   ![Capture d’écran de la fenêtre de Console de débogage Microsoft Visual Studio montrant la sortie’Hello Word ! ' et’Appuyez sur une touche pour fermer cette fenêtre'.](../media/vs-2019/overview-console-window.png)

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

1. Réexécutez l’application en sélectionnant **Déboguer** > **Démarrer sans débogage** ou en appuyant sur **CTRL** + **F5**.

   Visual Studio régénère l’application et une fenêtre de console s’ouvre et vous demande votre nom.

1. Entrez votre nom dans la fenêtre de console et appuyez sur **Entrée**.

   ![Capture d’écran de la fenêtre de Console de débogage Microsoft Visual Studio montrant l’invite d’un nom, l’entrée et la sortie’Hello Georgette ! '.](../media/vs-2019/overview-console-input.png)

1. Appuyez sur une touche pour fermer la fenêtre de console et arrêter le programme en cours d’exécution.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Utiliser la refactorisation et IntelliSense

Examinons comment la [refactorisation](../../ide/refactoring-in-visual-studio.md) et [IntelliSense](../../ide/using-intellisense.md) peuvent vous aider à coder plus efficacement au travers de deux ou trois exemples.

Tout d’abord, renommons la variable `name` :

1. Double-cliquez sur la variable `name` pour la sélectionner.

2. Tapez le nouveau nom de la variable, **username**.

   Notez qu’une zone grisée apparaît autour de la variable et qu’une ampoule s’affiche dans la marge.

::: moniker range="vs-2017"

3. Sélectionnez l’icône d’ampoule pour afficher les [Actions rapides](../../ide/quick-actions.md) disponibles. Sélectionnez **Renommer « name » en « username »**.

   ![Renommer une action dans Visual Studio](../media/rename-quick-action.png)

   La variable est renommée dans tout le projet, ce qui, dans notre cas, représente uniquement deux emplacements.

   ![Image GIF animée montrant la refactorisation du renommage dans Visual Studio](../media/rename-refactoring.gif)

::: moniker-end

::: moniker range=">=vs-2019"

3. Sélectionnez l’icône d’ampoule pour afficher les [Actions rapides](../../ide/quick-actions.md) disponibles. Sélectionnez **Renommer « name » en « username »**.

   ![Renommer une action dans Visual Studio](../media/vs-2019/rename-quick-action.png)

   La variable est renommée dans tout le projet, ce qui, dans notre cas, représente uniquement deux emplacements.

::: moniker-end

4. À présent, examinons IntelliSense. Sous la ligne indiquant `Console.WriteLine($"\nHello {username}!");`, tapez `DateTime now = DateTime.`.

   Une zone affiche les membres de la classe <xref:System.DateTime>. De plus, la description du membre actuellement sélectionné s’affiche dans une zone distincte.

   ![Liste des membres IntelliSense dans Visual Studio](../media/intellisense-list-members.png)

5. Sélectionnez le membre nommé **Now**, qui est une propriété de la classe, en double-cliquant dessus ou en appuyant sur la touche **Tab**. Complétez la ligne de code en ajoutant un point-virgule à la fin.

6. Au-dessous, tapez ou collez les lignes de code suivantes :

   ```csharp
   int dayOfYear = now.DayOfYear;

   Console.Write("Day of year: ");
   Console.WriteLine(dayOfYear);
   ```

   > [!TIP]
   > La méthode <xref:System.Console.Write%2A?displayProperty=nameWithType> est un peu différente de <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> dans la mesure où elle n’ajoute pas de marque de fin de ligne une fois imprimée. Cela signifie que la portion de texte suivante qui est envoyée à la sortie s’imprime sur la même ligne. Vous pouvez pointer sur chacune de ces méthodes dans votre code pour voir sa description.

7. Nous allons ensuite utiliser la refactorisation pour rendre le code un peu plus concis. Cliquez sur la variable `now` dans la ligne `DateTime now = DateTime.Now;`.

   Notez qu’une petite icône de tournevis apparaît dans la marge de cette ligne.

8. Cliquez sur l’icône de tournevis pour voir les suggestions disponibles dans Visual Studio. Dans le cas présent, il affiche la refactorisation de la [variable temporaire inline](../../ide/reference/inline-temporary-variable.md) pour supprimer une ligne de code sans changer le comportement global du code :

   ![Refactorisation de la variable temporaire inline dans Visual Studio](../media/inline-temporary-variable-refactoring.png)

9. Cliquez sur **Variable temporaire Inline** pour refactoriser le code.

::: moniker range="vs-2017"

10. Réexécutez le programme en appuyant sur **CTRL** + **F5**. La sortie ressemble à ceci :

    ! Capture d’écran de la fenêtre de console cmd.exe montrant l’invite d’un nom, l’entrée et la sortie «Hello Georgette ! Jour de l’année : 151 '.] (.. /Media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Réexécutez le programme en appuyant sur **CTRL** + **F5**. La sortie ressemble à ceci :

    ![Capture d’écran de la fenêtre de Console de débogage Microsoft Visual Studio montrant l’invite d’un nom, l’entrée et la sortie’Hello Georgette ! Jour de l’année : 43.](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code&quot;></a>Déboguer du code

Quand vous écrivez du code, vous devez l’exécuter et le tester pour rechercher les bogues. Le système de débogage de Visual Studio vous permet de parcourir le code instruction par instruction et d’en examiner les variables au fur et à mesure de votre avancement. Vous pouvez définir des *points d’arrêt* qui arrêtent l’exécution du code à une ligne particulière. Vous pouvez observer la façon dont la valeur d’une variable change à mesure que le code s’exécute, et bien plus encore.

Définissons un point d’arrêt pour voir la valeur de la variable `username` quand le programme est en cours.

1. Recherchez la ligne de code qui indique `Console.WriteLine($&quot;\nHello {username}!");`. Pour définir un point d’arrêt sur cette ligne de code, autrement dit, pour que l’exécution du programme soit suspendue au niveau de cette ligne, cliquez dans la bordure à l’extrême gauche de l’éditeur. Vous pouvez également cliquer n’importe où sur la ligne de code, puis appuyer sur **F9**.

   Un cercle rouge apparaît dans la bordure à gauche, et le code est surligné en rouge.

   ![Point d’arrêt sur une ligne de code dans Visual Studio](../media/breakpoint.png)

1. Démarrez le débogage **en sélectionnant déboguer**  >  **Démarrer le débogage** ou en appuyant sur **F5**.

1. Quand la fenêtre de console apparaît et vous demande votre nom, tapez-le, puis appuyez sur **Entrée**.

   Le focus retourne à l’éditeur de code Visual Studio et la ligne de code avec le point d’arrêt est surlignée en jaune. Cela signifie qu’il s’agit de la ligne de code suivante que le programme exécute.

1. Placez le pointeur de la souris sur la variable `username` pour afficher sa valeur. Vous pouvez également cliquer avec le bouton droit sur `username`, puis sélectionner **Ajouter un espion** pour ajouter la variable à la fenêtre **Espion**, dans laquelle vous pouvez également voir sa valeur.

   ![Valeur de la variable pendant le débogage dans Visual Studio](../media/debugging-variable-value.png)

1. Pour laisser le programme s’exécuter jusqu’à son terme, appuyez à nouveau sur **F5**.

Pour en savoir plus sur le processus de débogage de Visual Studio, consultez [Visite guidée des fonctionnalités de débogage](../../debugger/debugger-feature-tour.md).

## <a name="customize-visual-studio"></a>Personnaliser Visual Studio

Vous pouvez personnaliser l’interface utilisateur de Visual Studio, notamment changer le thème de couleur par défaut. Pour remplacer le thème par **Sombre** :

1. Dans la barre de menus, choisissez **Outils**  >  **options** pour ouvrir la boîte de dialogue **options** .

::: moniker range="vs-2017"

2. Dans la  > page options **générales** de l’environnement, remplacez la sélection du **thème de couleur** par **foncé**, puis cliquez sur **OK**.

   Le thème de couleur de l’ensemble de l’IDE devient **Sombre**.

   ![Visual Studio en thème sombre](../media/dark-theme.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Dans la  > page options **générales** de l’environnement, remplacez la sélection du **thème de couleur** par **foncé**, puis cliquez sur **OK**.

   Le thème de couleur de l’ensemble de l’IDE devient **Sombre**.

   ![Visual Studio en thème sombre](../media/vs-2019/dark-theme.png)

::: moniker-end

Pour en savoir plus sur les autres façons possibles de personnaliser l’IDE, consultez [Personnaliser Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).