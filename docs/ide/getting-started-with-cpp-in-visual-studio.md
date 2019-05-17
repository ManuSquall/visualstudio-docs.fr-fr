---
title: Bien démarrer avec C++
description: ''
ms.custom: mvc
ms.date: 12/04/2017
ms.topic: tutorial
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: 375879e6a6aba93b702c65412328458a9a5568ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62962811"
---
# <a name="get-started-with-c-in-visual-studio"></a>Bien démarrer avec C++ dans Visual Studio

Suivez ce guide de démarrage rapide pour vous familiariser avec la plupart des outils et boîtes de dialogue que vous pouvez utiliser quand vous développez des applications en C++ avec Visual Studio. Créez une application console du style « Hello, World » pour découvrir plus en détail comment utiliser l’IDE (environnement de développement intégré).

## <a name="prerequisites"></a>Prérequis

Pour suivre ce guide de démarrage rapide, vous n’avez pas besoin de connaître le langage C++, mais vous devez être familiarisé avec certains concepts généraux de la programmation et du débogage. La documentation Visual Studio n’est pas conçue pour vous apprendre la programmation en C++. Pour savoir où trouver des ressources d’apprentissage en C++, consultez la page [Get Started](https://isocpp.org/get-started) sur le site web ISO C++.

::: moniker range="vs-2017"

Pour ce guide de démarrage rapide, vous avez besoin de Visual Studio 2017 avec la charge de travail **Développement Desktop en C++** installée. Pour obtenir un guide d’installation rapide, consultez [Installer la prise en charge de C++ dans Visual Studio](/cpp/build/vscpp-step-0-installation).

::: moniker-end

::: moniker range=">=vs-2019"

Pour ce guide de démarrage rapide, vous avez besoin de Visual Studio 2019 avec la charge de travail **Développement Desktop en C++** installée. Pour obtenir un guide d’installation rapide, consultez [Installer la prise en charge de C++ dans Visual Studio](/cpp/build/vscpp-step-0-installation).

::: moniker-end

## <a name="create-a-console-app"></a>Créer une application console

S’il n’est pas déjà en cours d’exécution, ouvrez Visual Studio.

::: moniker range="vs-2017"

![IDE avec paramètres Visual C&#43;&#43; appliqués](../ide/media/get-started-cpp-ide-layout.png)

Après avoir ouvert Visual Studio, vous pouvez voir les trois composants de base de l’IDE : les fenêtres Outil, les menus et les barres d’outils, ainsi que l’espace de la fenêtre principale. Les fenêtres Outil sont ancrées sur les côtés gauche et droit de la fenêtre de l’application. La zone **Lancement rapide**, la barre de menus et la barre d’outils standard sont situées en haut de la fenêtre. La **page de démarrage** se trouve au centre de la fenêtre. Lorsque vous ouvrez une solution ou un projet, les éditeurs et les concepteurs apparaissent dans cet espace. Durant le développement d’une application, la plupart des opérations se passent dans cette zone centrale.

::: moniker-end

::: moniker range=">=vs-2019"

Une fois que vous avez ouvert Visual Studio, la fenêtre de démarrage apparaît en premier. Sélectionnez **Continuer sans code** pour ouvrir l’environnement de développement.

Vous allez voir les trois parties de base de l’IDE : les fenêtres Outils, les menus et barres d’outils ainsi que l’espace de la fenêtre principale. Les fenêtres Outil sont ancrées sur les côtés gauche et droit de la fenêtre de l’application. La zone de recherche, la barre de menus et la barre d’outils standard sont en haut. Quand vous chargez une solution ou un projet, les éditeurs et les concepteurs apparaissent dans l’espace central de la fenêtre d’application. Quand vous développez une application, vous passez la majeure partie de votre temps dans cette zone centrale.

::: moniker-end

Visual Studio organise le code des applications dans des *projets*, et vos projets dans des *solutions*. Un projet contient l’ensemble des options, des configurations et des règles utilisées pour créer une application. Il gère également le lien entre tous les fichiers d’un projet et les éventuels fichiers externes. Pour créer votre application, commencez par créer un projet et une solution.

### <a name="to-create-a-console-app-project"></a>Pour créer un projet d’application console

1. Dans la barre de menus, choisissez **Fichier > Nouveau > Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.

   ![Dans la barre de menus, choisir Fichier > Nouveau > Projet](../ide/media/get-started-cpp-file-new-project-menu.png)

1. Dans la boîte de dialogue **Nouveau projet**, sélectionnez **Installé > Visual C++** si ce n’est pas déjà fait. Dans le volet central, sélectionnez le modèle **Application console Windows**. Dans la zone d’édition **Nom**, entrez *HelloApp*.

   ![Utiliser la boîte de dialogue Nouveau projet pour créer votre projet d’application](../ide/media/get-started-cpp-new-project-dialog.png)

   Votre boîte de dialogue peut présenter des options différentes, selon les charges de travail et composants Visual Studio que vous avez installés. Si vous ne voyez pas les modèles de projet Visual C++, vous devez réexécuter le programme Visual Studio Installer et installer la charge de travail **Développement Desktop en C++**. Vous pouvez le faire directement à partir de la boîte de dialogue **Nouveau projet**. Pour lancer le programme Visual Studio Installer, choisissez le lien **Ouvrir Visual Studio Installer** dans la boîte de dialogue.

1. Choisissez le bouton **OK** pour créer le projet et la solution de votre application.

   La solution et le projet HelloApp, avec les fichiers de base d’une application console Windows, sont créés, puis automatiquement chargés dans **l’Explorateur de solutions**. Le fichier *HelloApp.cpp* s’ouvre dans l’éditeur de code. Ces éléments s’affichent dans **l’Explorateur de solutions** :

   ![Fichiers pour la solution dans Solution Explorer](../ide/media/get-started-cpp-solution-explorer.png)

## <a name="add-code-to-the-app"></a>Ajouter du code à l’application

Ensuite, vous devez ajouter le code nécessaire pour afficher le mot « Hello » dans la fenêtre de console.

### <a name="to-edit-code-in-the-editor"></a>Pour modifier le code dans l’éditeur

1. Dans le fichier *HelloApp.cpp*, insérez une ligne vide avant la ligne `return 0;`, puis entrez ce code :

   ```cpp
   cout << "Hello\n";
   ```

   Une ligne ondulée rouge s’affiche sous `cout`. Si vous placez le pointeur dessus, un message d’erreur s’affiche.

   ![Texte d'erreur pour cout](../ide/media/get-started-cpp-intellisense-error.png)

   Le message d’erreur s’affiche également dans la fenêtre **Liste d’erreurs** . Vous pouvez afficher cette fenêtre en choisissant **Affichage > Liste d’erreurs** dans la barre de menus.

   ![Erreur dans la fenêtre Liste d’erreurs](../ide/media/get-started-cpp-error-list.png)

   Dans votre code, il manque une déclaration pour [std::cout](/cpp/standard-library/iostream), qui se trouve dans le fichier d’en-tête *\<iostream>*.

1. Pour ajouter l’en-tête *iostream*, entrez ce code après `#include "stdafx.h"` :

   ```cpp
   #include <iostream>
   using namespace std;
   ```

   Vous avez sans doute remarqué qu’une zone est apparue quand vous avez commencé à entrer le code. Cette zone contient des suggestions de saisie semi-automatique pour les caractères que vous venez d’entrer. Il s’agit d’une option de la fonctionnalité IntelliSense C++, qui fournit des invites de codage, notamment des membres de classe ou d’interface et des informations sur les paramètres. Vous pouvez aussi utiliser des extraits de code, qui sont des blocs de code prédéfinis. Pour plus d’informations, consultez [Utilisation d’IntelliSense](../ide/using-intellisense.md) et [Extraits de code](../ide/code-snippets.md).

   ![Le code résolu dans l’éditeur](../ide/media/get-started-cpp-cout-fix.png)

   La ligne ondulée rouge sous `cout` disparaît lorsque vous corrigez l’erreur.

1. Pour enregistrer les modifications dans le fichier, appuyez sur **Ctrl+S**.

## <a name="build-the-app"></a>Générer l’application

Vous pouvez facilement générer votre code. Dans la barre de menus, choisissez **Générer > Générer la solution**. Visual Studio génère la solution HelloApp, tout en affichant l’avancement de l’opération dans la fenêtre **Sortie**.

   ![Générer la solution HelloApp](../ide/media/get-started-cpp-build-solution.gif)

## <a name="debug-and-test-the-app"></a>Déboguer et tester l’application

Vous pouvez déboguer HelloApp pour vérifier si le mot « Hello » s’affiche bien dans la fenêtre de console.

### <a name="to-debug-the-app"></a>Pour déboguer l'application

Pour démarrer le débogueur, choisissez **Déboguer > Démarrer le débogage** dans la barre de menus.

![Commande Démarrer le débogage du menu Débogage](../ide/media/get-started-cpp-start-debugging-menu.png)

Le débogueur démarre et exécute le code. La fenêtre de console (une fenêtre distincte qui ressemble à une invite de commandes) s’affiche pendant quelques secondes, mais se clôt rapidement lorsque le débogueur s’arrête en cours d’exécution. Pour afficher le texte, vous devez définir un point d’arrêt afin d’interrompre l’exécution du programme.

### <a name="to-add-a-breakpoint"></a>Pour ajouter un point d’arrêt

1. Dans l’éditeur, placez le curseur dans la ligne `return 0;`. Dans la barre de menus, choisissez **Déboguer > Basculer le point d’arrêt**. Vous pouvez également cliquer dans la marge de gauche pour définir un point d’arrêt.

     ![Commande Basculer le point d'arrêt du menu Débogage](../ide/media/get-started-cpp-toggle-breakpoint-menu.png)

     Un cercle rouge apparaît à côté de la ligne de code dans la bordure gauche de la fenêtre de l’éditeur.

     ![Point d’arrêt indiqué dans la marge de la fenêtre](../ide/media/get-started-cpp-breakpoint-set.png)

1. Pour démarrer le débogage, appuyez sur **F5**.

   Le débogueur démarre et une fenêtre de console apparaît avec le mot **Hello**.

   ![Texte Hello dans la fenêtre de console](../ide/media/get-started-cpp-helloapp-window.png)

1. Pour arrêter le débogage, appuyez sur **Maj+F5**.

Pour plus d’informations sur le débogage d’un projet de console, consultez [Projets de console](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a>Générer une version release de l’application

Maintenant que vous avez vérifié que tout fonctionne, vous pouvez préparer une version Release de l’application. Les versions de mise en production ne conservent pas les informations de débogage et utilisent des options d’optimisation du compilateur pour créer du code d’une taille plus petite et qui s’exécute plus vite.

### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Pour nettoyer les fichiers solution et générer une version Release

1. Dans la barre de menus, choisissez **Générer > Nettoyer la solution** pour supprimer les fichiers intermédiaires et les fichiers de sortie créés pendant les générations précédentes.

   ![Commande Nettoyer la solution du menu Générer](../ide/media/get-started-cpp-clean-solution-menu.png)

1. Pour changer la configuration de la solution HelloApp de **Debug** à **Release**, dans la barre d’outils, sélectionnez la liste déroulante du contrôle Configurations de solutions, puis choisissez **Release**.

   ![Générer une version Release de l'application](../ide/media/get-started-cpp-set-release-configuration.png)

1. Générez la solution. Dans la barre de menus, choisissez **Générer > Générer la solution**.

Quand cette génération est terminée, vous avez une nouvelle application prête à être copiée et exécutée dans une fenêtre d’invite de commandes. Cette application est très simple, mais il ne tient qu’à vous de créer des applications plus complexes.

Félicitations ! Vous avez terminé ce guide de démarrage rapide.

## <a name="see-also"></a>Voir aussi

- [Utilisation de l’IDE de Visual Studio pour le développement C++ pour poste de travail](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)
- [Procédure pas à pas : Créer une application simple avec C# ou Visual Basic](../get-started/csharp/tutorial-wpf.md)
- [Conseils de productivité pour Visual Studio](../ide/productivity-tips-for-visual-studio.md)
