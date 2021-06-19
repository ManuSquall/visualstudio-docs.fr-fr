---
title: Vue d’ensemble pour les développeurs Visual Basic
description: Apprenez à utiliser Visual Studio pour modifier, déboguer et générer du code, puis publiez une application en tant que développeur Visual Basic.
ms.date: 03/02/2021
ms.technology: vs-ide-general
ms.custom:
- vs-acquisition
- get-started
- SEO-VS-2020
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 486201d61f6bd2d149c9aea66efee1814ce667e7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386629"
---
# <a name="welcome-to-the-visual-studio-ide--visual-basic"></a>Bienvenue dans l’IDE Visual Studio | Visual Basic

*L’environnement de développement intégré* de Visual Studio est une plateforme de lancement créative avec laquelle vous pouvez modifier, déboguer et générer du code, puis publier une application. Un environnement de développement intégré (IDE) est un programme riche en fonctionnalités qui peut être utilisé pour de nombreux aspects du développement de logiciels. Au-delà de l’éditeur et du débogueur standard fournis par la plupart des IDE, Visual Studio inclut des compilateurs, des outils de complétion de code, des concepteurs graphiques et de nombreuses autres fonctionnalités afin de faciliter le processus de développement logiciel.

::: moniker range="vs-2017"

![IDE de Visual Studio](../media/visual-studio-ide.png)

::: moniker-end

::: moniker range=">=vs-2019"

[![IDE Visual Studio 2019](media/vs-2019/ide-overview.png)](media/vs-2019/ide-overview.png#lightbox)

::: moniker-end

Cette image montre Visual Studio avec un projet ouvert et plusieurs fenêtres Outil principales dont vous êtes susceptible de vous servir :

- L’[Explorateur de solutions](../../ide/solutions-and-projects-in-visual-studio.md) (en haut à droite) vous permet d’afficher, de parcourir et de gérer vos fichiers de code. **Explorateur de solutions** pouvez vous aider à organiser votre code en regroupant les fichiers dans des [solutions et des projets](tutorial-projects-solutions.md).

- La [fenêtre de l’éditeur](../../ide/writing-code-in-the-code-and-text-editor.md) (au centre), où vous passerez sans doute la plupart de votre temps, affiche le contenu des fichiers. C’est là que vous pouvez modifier le code ou concevoir une interface utilisateur telle qu’une fenêtre avec des boutons et des zones de texte.

- La [fenêtre Sortie](../../ide/reference/output-window.md) (en bas au centre) est l’emplacement où Visual Studio envoie des notifications telles que les messages d’erreur et de débogage, les avertissements du compilateur, les messages d’état de publication, entre autres. Chaque source de message a son propre onglet.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts&preserve-view=true) (en bas à droite) vous permet de suivre des éléments de travail et de partager du code avec d’autres utilisateurs à l’aide des technologies de gestion de versions comme [Git](https://git-scm.com/) et [Team Foundation Version Control (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts&preserve-view=true).

## <a name="editions"></a>Éditions

Visual Studio est disponible pour Windows et Mac. [Visual Studio pour Mac](/visualstudio/mac/) compte de nombreuses fonctionnalités en commun avec Visual Studio 2017, et est optimisé pour le développement d’applications mobiles et multiplateformes. Cet article traite essentiellement de la version Windows de Visual Studio 2017.

Il existe trois éditions de Visual Studio 2017 : Community, Professional et Enterprise. Consultez [Comparez les IDE Visual Studio 2017](https://visualstudio.microsoft.com/vs/compare/) pour en savoir plus sur les fonctionnalités prises en charge dans chaque édition.

## <a name="popular-productivity-features"></a>Fonctionnalités de productivité populaires

Voici quelques-unes des fonctionnalités populaires de Visual Studio qui vous aident à être plus productifs quand vous développez des logiciels :

- Tildes et [Actions rapides](../../ide/quick-actions.md)

   Les tildes sont des soulignements ondulés qui vous signalent des erreurs ou des problèmes potentiels dans votre code en cours de frappe. Ces indices visuels permettent de résoudre les problèmes immédiatement sans attendre que l’erreur soit découverte durant la génération ou quand vous exécutez le programme. Si vous pointez sur un tilde, vous voyez des informations supplémentaires sur l’erreur. Une ampoule (appelée Action rapide) peut également apparaître dans la marge gauche, avec des actions pour corriger l’erreur.

   ::: moniker range="vs-2017"

   ![Tildes dans Visual Studio](media/squiggles-error.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Tildes dans Visual Studio](media/vs-2019/squiggles-error.png)

   ::: moniker-end

- [Refactorisation](../../ide/refactoring-in-visual-studio.md)

   La refactorisation inclut des opérations telles que le renommage intelligent des variables, l’extraction d’une ou plusieurs lignes de code dans une nouvelle méthode, le changement de l’ordre des paramètres de méthode, et bien plus encore.

   ::: moniker range="vs-2017"

   ![Menu Refactorisation dans Visual Studio](media/refactoring-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Menu Refactorisation dans Visual Studio](media/vs-2019/refactorings-menu.png)

   ::: moniker-end

- [IntelliSense](../../ide/using-intellisense.md)

   IntelliSense est un terme désignant un ensemble de fonctionnalités qui affichent des informations relatives au code directement dans l’éditeur et qui, dans certains cas, écrivent de petits bouts de code à votre place. Cela revient à avoir de la documentation de base incluse dans l’éditeur, ce qui vous évite d’avoir à rechercher ailleurs des informations sur les types. Les fonctionnalités d'IntelliSense varient selon le langage. Pour plus d’informations, consultez [C# IntelliSense](../../ide/visual-csharp-intellisense.md), [Visual C++ IntelliSense](../../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../../ide/javascript-intellisense.md) et [Visual Basic IntelliSense](../../ide/visual-basic-specific-intellisense.md). L’illustration suivante montre comment IntelliSense affiche une liste des membres d’un type :

   ::: moniker range="vs-2017"

   ![Liste des membres Visual Studio](media/intellisense-list-members.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Liste des membres Visual Studio](media/vs-2019/intellisense-list-members.png)

   ::: moniker-end

- Zone de recherche

   La maîtrise de Visual Studio peut sembler insurmontable parfois, avec autant de menus, d’options et de propriétés. La zone de recherche est un excellent moyen de trouver rapidement ce dont vous avez besoin dans Visual Studio. Quand vous commencez à taper le nom d’un élément que vous recherchez, Visual Studio affiche des résultats qui vous mènent exactement où vous devez accéder. Pour ajouter des fonctionnalités à Visual Studio, par exemple la prise en charge d’un langage de programmation supplémentaire, la zone de recherche fournit des résultats qui ouvrent Visual Studio Installer afin d’installer une charge de travail ou un composant spécifique.

   > [!TIP]
   > Appuyez sur **CTRL** + **Q** comme raccourci vers la zone de recherche.

   ::: moniker range="vs-2017"

   ![Zone de recherche Lancement rapide dans Visual Studio 2017](../media/quick-launch-nuget.png)

   Pour plus d’informations, consultez [Lancement rapide](../../ide/reference/quick-launch-environment-options-dialog-box.md).

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Zone de recherche dans Visual Studio 2019](media/vs-2019/quick-launch.png)

   ::: moniker-end

- [Live Share](/visualstudio/liveshare/)

   Modifiez et déboguez de manière collaborative avec d’autres utilisateurs en temps réel, quel que soit le type de votre application ou le langage de programmation. Vous pouvez partager instantanément et en toute sécurité votre projet puis partager au besoin des sessions de débogage, des instances de terminal, des applications web localhost, des appels vocaux, etc.

- [Hiérarchie d'appels](../../ide/reference/call-hierarchy.md)

   La fenêtre **Hiérarchie d’appels** affiche les méthodes qui appellent une méthode sélectionnée. Ces informations peuvent être utiles quand vous envisagez de changer ou de supprimer la méthode, ou quand vous essayez de repérer un bogue.

   ::: moniker range="vs-2017"

   ![Fenêtre Hiérarchie d’appels dans Visual Studio](media/call-hierarchy.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Fenêtre Hiérarchie d’appels dans Visual Studio](media/vs-2019/call-hierarchy.png)

   ::: moniker-end

- [CodeLens](../../ide/find-code-changes-and-other-history-with-codelens.md)

   CodeLens vous aide à rechercher les références à votre code, les modifications apportées à votre code, les bogues liés, les éléments de travail, les revues de code et les tests unitaires, tout cela sans quitter l’éditeur.

   ::: moniker range="vs-2017"

   ![CodeLens dans Visual Studio](media/codelens.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![CodeLens dans Visual Studio](media/vs-2019/codelens.png)

   ::: moniker-end

- [Atteindre la définition](../../ide/go-to-and-peek-definition.md)

   La fonctionnalité Atteindre la définition vous mène directement à l’emplacement où une fonction ou un type est défini(e).

   ::: moniker range="vs-2017"

   ![Atteindre la définition dans Visual Studio 2017](media/go-to-definition-menu.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Atteindre la définition dans Visual Studio 2019](media/vs-2019/go-to-definition-menu.png)

   ::: moniker-end

- [Aperçu de définition](../../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

   La fenêtre **Aperçu de définition** montre la définition d’une méthode ou d’un type sans réellement ouvrir un fichier distinct.

   ::: moniker range="vs-2017"

   ![Aperçu de définition dans Visual Studio](media/peek-definition.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Aperçu de définition dans Visual Studio](media/vs-2019/peek-definition.png)

   ::: moniker-end

## <a name="install-the-visual-studio-ide"></a>Installer l’IDE de Visual Studio

Dans cette section, vous allez créer un projet simple afin d’essayer des actions que vous pouvez réaliser avec Visual Studio. Vous allez modifier le thème de couleur, utiliser [IntelliSense](../../ide/using-intellisense.md) comme aide au codage, déboguer une application pour afficher la valeur d’une variable pendant l’exécution du programme.

::: moniker range="vs-2017"

Pour commencer, [téléchargez Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) et installez-le sur votre système. Le programme d’installation modulaire vous permet de sélectionner et d’installer des *charges de travail*, qui sont des groupes de fonctionnalités nécessaires pour la plateforme ou le langage de programmation que vous préférez. Pour suivre les étapes de [création d’un programme](#create-a-program), veillez à sélectionner la charge de travail **Développement multiplateforme .NET Core** pendant l’installation.

::: moniker-end

::: moniker range=">=vs-2019"

Pour commencer, [téléchargez Visual Studio](https://visualstudio.microsoft.com/downloads) et installez-le sur votre système. Le programme d’installation modulaire vous permet de sélectionner et d’installer des *charges de travail*, qui sont des groupes de fonctionnalités nécessaires pour la plateforme ou le langage de programmation que vous préférez. Pour suivre les étapes de [création d’un programme](#create-a-program), veillez à sélectionner la charge de travail **Développement multiplateforme .NET Core** pendant l’installation.

::: moniker-end

![Charge de travail Développement multiplateforme .NET Core dans Visual Studio Installer](../media/dotnet-core-cross-platform-workload.png)

Lorsque vous ouvrez Visual Studio pour la première fois, vous pouvez vous [connecter](../../ide/signing-in-to-visual-studio.md) avec votre compte Microsoft ou avec votre compte professionnel ou scolaire.

## <a name="customize-visual-studio"></a>Personnaliser Visual Studio

Vous pouvez personnaliser l’interface utilisateur de Visual Studio, notamment changer le thème de couleur par défaut.

### <a name="change-the-color-theme"></a>Changer le thème de couleur

Pour remplacer le thème par **Sombre** :

::: moniker range="vs-2017"

1. Ouvrez Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio. Dans la fenêtre Démarrer, sélectionnez **continuer sans code**.


    :::image type="content" source="media/vs-2019/continue-without-code.png" alt-text="Capture d’écran de la fenêtre de démarrage dans Visual Studio 2019, avec le lien « continuer sans code » mis en surbrillance.":::

   L’IDE s’ouvre.

::: moniker-end

2. Dans la barre de menus, choisissez **Outils**  >  **options** pour ouvrir la boîte de dialogue **options** .

3. Dans la   >  page options **générales** de l’environnement, remplacez la sélection **thème de couleur** par **foncé**, puis cliquez sur **OK**.

   ![Basculer vers le thème de couleur sombre dans Visual Studio](media/change-color-theme.png)

   Le thème de couleur de l’ensemble de l’IDE devient **Sombre**.

   ::: moniker range="vs-2017"

   ![Visual Studio en thème sombre](../../ide/media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Visual Studio en thème sombre](media/vs-2019/dark-theme.png)

   ::: moniker-end

### <a name="select-environment-settings"></a>Sélectionner les paramètres d’environnement

Ensuite, nous allons configurer Visual Studio pour utiliser les paramètres d’environnement adaptés aux développeurs Visual Basic.

1. Dans la barre de menus, choisissez **Outils**  >  **importation et exportation de paramètres**.

2. Dans l' **Assistant importation et exportation de paramètres**, sélectionnez **Réinitialiser tous les paramètres** sur la première page, puis cliquez sur **suivant**.

3. Sur la page **enregistrer les paramètres actuels** , sélectionnez une option pour enregistrer vos paramètres actuels, puis cliquez sur **suivant**. (Si vous n’avez personnalisé aucun paramètre, sélectionnez **Non, réinitialiser simplement les paramètres en remplaçant mes paramètres actuels**.)

4. Sur la page **choisir une collection de paramètres par défaut** , choisissez **Visual Basic**, puis cliquez sur **Terminer**.

5. Dans la page **réinitialisation terminée** , cliquez sur **Fermer**.

Pour en savoir plus sur les autres façons possibles de personnaliser l’IDE, consultez [Personnaliser Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="create-a-program"></a>Créer un programme

Nous allons aller plus loin en créant un programme simple.

::: moniker range="vs-2017"

1. Dans la barre de menus de Visual Studio, choisissez **fichier** > **nouveau projet**.

   ![Fichier > Nouveau projet sur la barre de menus](media/file-new-project-menu.png)

   La boîte **de dialogue Nouveau projet** affiche plusieurs *modèles* de projet. Un modèle contient les fichiers et les paramètres de base nécessaires pour un type de projet donné.

1. Choisissez la catégorie **.NET Core** sous **Visual Basic**, puis choisissez le modèle **Application console (.NET Core)**. Dans la zone de texte **Nom**, tapez **HelloWorld**, puis cliquez sur le bouton **OK**.

   ![Modèle d’application .NET Core](media/overview-npd.png)

   > [!NOTE]
   > Si vous la catégorie **. NET Core** ne s’affiche pas, vous devez installer la charge de travail **Développement multiplateforme .NET Core**. Pour cela, cliquez sur le lien **Ouvrir Visual Studio Installer** en bas à gauche de la boîte de dialogue **Nouveau projet**. Une fois Visual Studio Installer ouvert, faites défiler l’écran vers le bas pour sélectionner la charge de travail **Développement multiplateforme .NET Core**, puis sélectionnez **Modifier**.

   Visual Studio crée le projet. Il s’agit d’une application « Hello world » simple, qui appelle la méthode <xref:System.Console.WriteLine?displayProperty=nameWithType> pour afficher la chaîne littérale « Hello World! » dans la fenêtre de console (sortie du programme).

   Quelque chose qui ressemble à ce qui suit doit s’afficher :

   ![Environnement IDE de Visual Studio](media/overview-ide-console-app.png)

   Le code Visual Basic de l’application apparaît dans la fenêtre d’éditeur, qui occupe la majeure partie de l’espace. Notez que le texte est colorisé automatiquement pour indiquer les différentes parties du code, comme les mots clés et les types. En outre, les petites lignes en pointillés verticales du code indiquent les accolades correspondant entre elles et les numéros de ligne vous aident à localiser le code. Vous pouvez cliquer sur les signes moins encadrés pour réduire ou développer des blocs de code. Cette fonctionnalité de surlignage de code vous permet de masquer le code dont vous n’avez pas besoin, ce qui contribue à réduire l’encombrement à l’écran. Vos fichiers projet sont répertoriés sur le côté droit dans une fenêtre appelée **Explorateur de solutions**.

   ![IDE de Visual Studio avec zones rouges](media/overview-ide-console-app-red-boxes.png)

   Il existe d’autres menus et fenêtres d’outil, que nous aborderons par la suite.

1. Maintenant, démarrez l’application. Pour ce faire, vous pouvez choisir **Démarrer sans débogage** dans le menu **Déboguer** de la barre de menus. Vous pouvez également appuyer sur **CTRL** + **F5**.

   ![Menu Déboguer > Démarrer sans débogage](../media/overview-start-without-debugging.png)

   Visual Studio génère l’application, et une fenêtre de console s’ouvre avec le message **Hello World!**. Maintenant, votre application fonctionne !

   ![Fenêtre de console](../media/overview-console-window.png)

1. Appuyez sur une touche au hasard pour fermer la fenêtre de console.

1. Ajoutons du code supplémentaire à l’application. Ajoutez le code Visual Basic suivant avant la ligne qui indique `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Ce code affiche **What is your name?** dans la fenêtre de console, puis attend que l’utilisateur entre du texte suivi de la touche **Entrée**.

1. Remplacez la ligne qui indique `Console.WriteLine("Hello World!")` par le code suivant :

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Exécutez à nouveau l’application en appuyant sur **CTRL** + **F5**.

   Visual Studio régénère l’application et une fenêtre de console s’ouvre et vous demande votre nom.

1. Entrez votre nom dans la fenêtre de console et appuyez sur **Entrée**.

   ![Entrée de la fenêtre de console](../media/overview-console-input.png)

1. Appuyez sur une touche pour fermer la fenêtre de console et arrêter le programme en cours d’exécution.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans la barre de menus de Visual Studio, choisissez **fichier**  >  **nouveau**  >  **projet**. (Vous pouvez également appuyer sur **CTRL** + **MAJ** + **N**.)

    :::image type="content" source="media/vs-2019/file-new-project.png" alt-text="Capture d’écran du fichier > nouvelle > sélection de projet à partir de la barre de menus de Visual Studio 2019.":::

   La fenêtre **Créer un projet** s’affiche et présente plusieurs *modèles* de projet. Un modèle contient les fichiers et les paramètres de base requis pour un type de projet donné.

1. Pour rechercher le modèle souhaité, tapez ou entrez **console .net core** dans la zone de recherche. La liste des modèles disponibles est automatiquement filtrée en fonction des mots clés que vous avez entrés. Vous pouvez filtrer davantage les résultats du modèle en choisissant **Visual Basic** dans la liste déroulante **tous les langages** , **Windows** dans la liste **toutes les plateformes** et la **console** dans la liste tous les **types de projets** .

   Sélectionnez le modèle **application console** , puis cliquez sur **suivant**.

    :::image type="content" source="media/vs-2019/create-new-project.png" alt-text="Capture d’écran de la fenêtre créer un nouveau projet dans Visual Studio 2019, où vous sélectionnez le modèle souhaité.":::

1. Dans la fenêtre **configurer votre nouveau projet** , entrez **HelloWorld** dans la zone **nom du projet** , modifiez éventuellement l’emplacement du répertoire pour vos fichiers projet (les paramètres régionaux par défaut sont `C:\Users\<name>\source\repos` ), puis cliquez sur **suivant**.

    :::image type="content" source="media/vs-2019/configure-new-project.png" alt-text="Capture d’écran de la fenêtre « configurer votre nouveau projet » dans Visual Studio 2019, où vous entrez le nom du projet.":::

1. Dans la fenêtre **informations supplémentaires** , vérifiez que **.net Core 3,1** s’affiche dans le menu déroulant **Framework cible** , puis cliquez sur **créer**.

    :::image type="content" source="media/vs-2019/create-project-additional-info.png" alt-text="Capture d’écran de la fenêtre « informations supplémentaires » dans Visual Studio 2019, où vous sélectionnez la version de .NET Core Framework que vous souhaitez.":::

   Visual Studio crée le projet. Il s’agit d’une application « Hello world » simple, qui appelle la méthode <xref:System.Console.WriteLine?displayProperty=nameWithType> pour afficher la chaîne littérale « Hello World! » dans la fenêtre de console (sortie du programme).

   Quelque chose qui ressemble à ce qui suit doit s’afficher :

   ![Environnement IDE de Visual Studio](media/overview-ide-console-app.png)

   Le code Visual Basic de l’application apparaît dans la fenêtre d’éditeur, qui occupe la majeure partie de l’espace. Notez que le texte est colorisé automatiquement pour indiquer les différentes parties du code, comme les mots clés et les types. En outre, les petites lignes en pointillés verticales du code indiquent les accolades correspondant entre elles et les numéros de ligne vous aident à localiser le code. Vous pouvez cliquer sur les signes moins encadrés pour réduire ou développer des blocs de code. Cette fonctionnalité de surlignage de code vous permet de masquer le code dont vous n’avez pas besoin, ce qui contribue à réduire l’encombrement à l’écran. Vos fichiers projet sont répertoriés sur le côté droit dans une fenêtre appelée **Explorateur de solutions**.

   ![IDE de Visual Studio avec zones rouges](media/overview-ide-console-app-red-boxes.png)

   Il existe d’autres menus et fenêtres d’outil, que nous aborderons par la suite.

1. Maintenant, démarrez l’application. Pour ce faire, vous pouvez choisir **Démarrer sans débogage** dans le menu **Déboguer** de la barre de menus. Vous pouvez également appuyer sur **CTRL** + **F5**.

   ![Menu Déboguer > Démarrer sans débogage](media/vs-2019/start-without-debugging.png)

   Visual Studio génère l’application, et une fenêtre de console s’ouvre avec le message **Hello World!**. Maintenant, votre application fonctionne !

   ![Capture d’écran de la fenêtre de console montrant le message de Hello World.](../media/vs-2019/overview-console-window.png)

1. Appuyez sur une touche au hasard pour fermer la fenêtre de console.

1. Ajoutons du code supplémentaire à l’application. Ajoutez le code Visual Basic suivant avant la ligne qui indique `Console.WriteLine("Hello World!")` :

   ```vb
   Console.WriteLine("What is your name?")
   Dim name = Console.ReadLine()
   ```

   Ce code affiche **What is your name?** dans la fenêtre de console, puis attend que l’utilisateur entre du texte suivi de la touche **Entrée**.

1. Remplacez la ligne qui indique `Console.WriteLine("Hello World!")` par le code suivant :

   ```vb
   Console.WriteLine("Hello " + name + "!")
   ```

1. Exécutez à nouveau l’application en appuyant sur **CTRL** + **F5**.

   Visual Studio régénère l’application et une fenêtre de console s’ouvre et vous demande votre nom.

1. Entrez votre nom dans la fenêtre de console et appuyez sur **Entrée**.

   ![Capture d’écran de la fenêtre de console montrant la question qu’est-ce que votre nom et la réponse de l’application.](../media/vs-2019/overview-console-input.png)

1. Appuyez sur une touche pour fermer la fenêtre de console et arrêter le programme en cours d’exécution.

::: moniker-end

## <a name="use-refactoring-and-intellisense"></a>Utiliser la refactorisation et IntelliSense

Examinons comment la [refactorisation](../../ide/refactoring-in-visual-studio.md) et [IntelliSense](../../ide/using-intellisense.md) peuvent vous aider à coder plus efficacement au travers de deux ou trois exemples.

Tout d’abord, renommons la variable `name` :

1. Double-cliquez sur la variable `name` pour la sélectionner.

2. Tapez le nouveau nom de la variable, **username**.

   Notez qu’une zone grisée apparaît autour de la variable et qu’une ampoule s’affiche dans la marge.

3. Sélectionnez l’icône d’ampoule pour afficher les [Actions rapides](../../ide/quick-actions.md) disponibles. Sélectionnez **Renommer « name » en « username »**.

   ![Renommer une action dans Visual Studio](media/rename-quick-action.png)

   La variable est renommée dans tout le projet, ce qui, dans notre cas, représente uniquement deux emplacements.

4. À présent, examinons IntelliSense. Sous la ligne indiquant `Console.WriteLine("Hello &quot; + username + &quot;!")`, tapez le fragment de code suivant :

    ```vb
   Dim now = Date.
   ```

   Une zone affiche les membres de la classe <xref:System.DateTime>. De plus, la description du membre actuellement sélectionné s’affiche dans une zone distincte.

   ![Liste des membres IntelliSense dans Visual Studio](media/intellisense-list-members.png)

5. Sélectionnez le membre nommé **Now**, qui est une propriété de la classe, en double-cliquant dessus ou en le sélectionnant à l’aide des touches de direction puis en appuyant sur **Tab**.

6. Au-dessous, tapez ou collez les lignes de code suivantes :

   ```vb
   Dim dayOfYear = now.DayOfYear
   Console.Write("Day of year: ")
   Console.WriteLine(dayOfYear)
   ```

   > [!TIP]
   > La méthode <xref:System.Console.Write%2A?displayProperty=nameWithType> est un peu différente de <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> dans la mesure où elle n’ajoute pas de marque de fin de ligne une fois imprimée. Cela signifie que la portion de texte suivante qui est envoyée à la sortie s’imprime sur la même ligne. Vous pouvez pointer sur chacune de ces méthodes dans votre code pour voir sa description.

7. Nous allons ensuite utiliser la refactorisation pour rendre le code un peu plus concis. Cliquez sur la variable `now` dans la ligne `Dim now = Date.Now`.

   Notez qu’une petite icône de tournevis apparaît dans la marge de cette ligne.

8. Cliquez sur l’icône de tournevis pour voir les suggestions disponibles dans Visual Studio. Dans le cas présent, il affiche la refactorisation de la [variable temporaire inline](../../ide/reference/inline-temporary-variable.md) pour supprimer une ligne de code sans changer le comportement global du code :

   ![Refactorisation de la variable temporaire inline dans Visual Studio](media/inline-temporary-variable-refactoring.png)

9. Cliquez sur **Variable temporaire Inline** pour refactoriser le code.

::: moniker range="vs-2017"

10. Réexécutez le programme en appuyant sur **CTRL** + **F5**. La sortie ressemble à ceci :

    ![Fenêtre de console avec la sortie du programme](../media/overview-console-final.png)

::: moniker-end

::: moniker range=">=vs-2019"

10. Réexécutez le programme en appuyant sur **CTRL** + **F5**. La sortie ressemble à ceci :

    ![Fenêtre de console avec la sortie du programme](../media/vs-2019/overview-console-final.png)

::: moniker-end

## <a name="debug-code&quot;></a>Déboguer du code

Quand vous écrivez du code, vous devez l’exécuter et le tester pour rechercher les bogues. Le système de débogage de Visual Studio vous permet de parcourir le code instruction par instruction et d’en examiner les variables au fur et à mesure de votre avancement. Vous pouvez définir des *points d’arrêt* qui arrêtent l’exécution du code à une ligne particulière. Vous pouvez observer la façon dont la valeur d’une variable change à mesure que le code s’exécute, et bien plus encore.

Définissons un point d’arrêt pour voir la valeur de la variable `username` quand le programme est en cours.

1. Recherchez la ligne de code qui indique `Console.WriteLine(&quot;Hello &quot; + username + &quot;!")`. Pour définir un point d’arrêt sur cette ligne de code, autrement dit, pour que l’exécution du programme soit suspendue au niveau de cette ligne, cliquez dans la bordure à l’extrême gauche de l’éditeur. Vous pouvez également cliquer n’importe où sur la ligne de code, puis appuyer sur **F9**.

   Un cercle rouge apparaît dans la bordure à gauche, et le code est surligné en rouge.

   ![Point d’arrêt sur une ligne de code dans Visual Studio](media/breakpoint.png)

1. Démarrez le débogage **en sélectionnant déboguer**  >  **Démarrer le débogage** ou en appuyant sur **F5**.

1. Quand la fenêtre de console apparaît et vous demande votre nom, tapez-le, puis appuyez sur **Entrée**.

   Le focus retourne à l’éditeur de code Visual Studio et la ligne de code avec le point d’arrêt est surlignée en jaune. Cela signifie qu’il s’agit de la ligne de code suivante que le programme exécute.

1. Placez le pointeur de la souris sur la variable `username` pour afficher sa valeur. Vous pouvez également cliquer avec le bouton droit sur `username`, puis sélectionner **Ajouter un espion** pour ajouter la variable à la fenêtre **Espion**, dans laquelle vous pouvez également voir sa valeur.

   ![Valeur de la variable pendant le débogage dans Visual Studio](media/debugging-variable-value.png)

1. Pour laisser le programme s’exécuter jusqu’à son terme, appuyez à nouveau sur **F5**.

Pour en savoir plus sur le processus de débogage de Visual Studio, consultez [Visite guidée des fonctionnalités de débogage](../../debugger/debugger-feature-tour.md).

## <a name="next-steps"></a>Étapes suivantes

Explorez davantage Visual Studio en suivant l’un de ces articles d’introduction :

> [!div class="nextstepaction"]
> [Apprendre à utiliser l’éditeur de code](tutorial-editor.md)

> [!div class="nextstepaction"]
> [Découvrir les projets et les solutions](tutorial-projects-solutions.md)

## <a name="see-also"></a>Voir aussi

- Découvrir d’[autres fonctionnalités de Visual Studio](../../ide/advanced-feature-overview.md)
- Visiter [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Lire le [blog Visual Studio](https://devblogs.microsoft.com/visualstudio/)
