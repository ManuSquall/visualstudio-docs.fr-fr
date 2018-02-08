---
title: "Bien démarrer avec C++ dans Visual Studio | Microsoft Docs"
ms.custom: mvc
ms.date: 12/04/2017
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: get-started-article
author: corob-msft
ms.author: tglee
manager: ghogen
dev_langs:
- CPP
ms.workload:
- cplusplus
ms.openlocfilehash: 2e0e0709b8a1737e3f78268ec324d4481dac285a
ms.sourcegitcommit: b18844078a30d59014b48a9c247848dea188b0ee
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2018
---
# <a name="get-started-with-c-in-visual-studio"></a>Bien démarrer avec C++ dans Visual Studio

Suivez ce guide de démarrage rapide pour vous familiariser avec la plupart des outils et boîtes de dialogue que vous pouvez utiliser quand vous développez des applications en C++ avec Visual Studio. Créez une application console du style « Hello, World » pour découvrir plus en détail comment utiliser l’IDE (environnement de développement intégré).

## <a name="prerequisites"></a>Prérequis

Pour suivre ce guide de démarrage rapide, vous n’avez pas besoin de connaître le langage C++, mais vous devez être familiarisé avec certains concepts généraux de la programmation et du débogage. La documentation Visual Studio n’est pas conçue pour vous apprendre la programmation en C++. Pour savoir où trouver des ressources d’apprentissage en C++, consultez la page [Get Started](https://isocpp.org/get-started) sur le site web ISO C++.

Pour ce guide de démarrage rapide, vous avez besoin de Visual Studio 2017 version 15.3 ou ultérieure, avec la charge de travail **Développement Desktop en C++** installée. Pour obtenir un guide d’installation rapide, consultez [Installer la prise en charge de C++ dans Visual Studio](/cpp/build/vscpp-step-0-installation).

## <a name="create-a-console-app"></a>Créer une application console

Démarrez Visual Studio, s’il y a lieu.

![IDE avec les paramètres Visual C&#43;&#43; appliqués](../ide/media/get-started-cpp-ide-layout.png "IDE avec les paramètres Visual C&#43;&#43; appliqués")

Après avoir ouvert Visual Studio, vous pouvez voir les trois composants de base de l’IDE : les fenêtres Outil, les menus et les barres d’outils, ainsi que l’espace de la fenêtre principale. Les fenêtres Outil sont ancrées sur les côtés gauche et droit de la fenêtre de l’application. La zone **Lancement rapide**, la barre de menus et la barre d’outils standard sont situées en haut de la fenêtre. La **page de démarrage** se trouve au centre de la fenêtre. Lorsque vous ouvrez une solution ou un projet, les éditeurs et les concepteurs apparaissent dans cet espace. Durant le développement d’une application, la plupart des opérations se passent dans cette zone centrale.

Visual Studio organise le code des applications dans des *projets*, et vos projets dans des *solutions*. Un projet contient l’ensemble des options, des configurations et des règles utilisées pour créer une application. Il gère également le lien entre tous les fichiers d’un projet et les éventuels fichiers externes. Pour créer votre application, commencez par créer un projet et une solution.

### <a name="to-create-a-console-app-project"></a>Pour créer un projet d’application console

1. Dans la barre de menus, choisissez **Fichier > Nouveau > Projet** pour ouvrir la boîte de dialogue **Nouveau projet**.

   ![Dans la barre de menus, choisir Fichier > Nouveau > Projet](../ide/media/get-started-cpp-file-new-project-menu.png "Dans la barre de menus, choisir Fichier > Nouveau > Projet")

1. Dans la boîte de dialogue **Nouveau projet**, sélectionnez **Installé > Visual C++** si ce n’est pas déjà fait. Dans le volet central, sélectionnez le modèle **Application console Windows**. Dans la zone d’édition **Nom**, entrez *HelloApp*.

   ![Utiliser la boîte de dialogue Nouveau projet pour créer votre projet d’application](../ide/media/get-started-cpp-new-project-dialog.png "Utiliser la boîte de dialogue Nouveau projet pour créer votre projet d’application")

   Votre boîte de dialogue peut présenter des options différentes, selon les charges de travail et composants Visual Studio que vous avez installés. Si vous ne voyez pas les modèles de projet Visual C++, vous devez réexécuter le programme Visual Studio Installer et installer la charge de travail **Développement Desktop en C++**. Vous pouvez le faire directement à partir de la boîte de dialogue **Nouveau projet**. Pour lancer le programme Visual Studio Installer, choisissez le lien **Ouvrir Visual Studio Installer** dans la boîte de dialogue.

1. Choisissez le bouton **OK** pour créer le projet et la solution de votre application.

   La solution et le projet HelloApp, avec les fichiers de base d’une application console Windows, sont créés, puis automatiquement chargés dans **l’Explorateur de solutions**. Le fichier HelloApp.cpp s’ouvre dans l’éditeur de code. Ces éléments s’affichent dans **l’Explorateur de solutions** :

   ![Fichiers de la solution dans l’Explorateur de solutions](../ide/media/get-started-cpp-solution-explorer.png "Fichiers de la solution dans l’Explorateur de solutions")

## <a name="add-code-to-the-app"></a>Ajouter du code à l’application

Ensuite, vous devez ajouter le code nécessaire pour afficher le mot « Hello » dans la fenêtre de console.

### <a name="to-edit-code-in-the-editor"></a>Pour modifier le code dans l’éditeur

1. Dans le fichier HelloApp.cpp, insérez une ligne vide avant la ligne `return 0;`, puis entrez ce code :

   ```cpp
   cout << "Hello\n";
   ```

   Une ligne ondulée rouge s’affiche sous `cout`. Si vous placez le pointeur dessus, un message d’erreur s’affiche.

   ![Texte d’erreur pour cout](../ide/media/get-started-cpp-intellisense-error.png "Texte d’erreur pour cout")

   Le message d’erreur s’affiche également dans la fenêtre **Liste d’erreurs** . Vous pouvez afficher cette fenêtre en choisissant **Affichage > Liste d’erreurs** dans la barre de menus.

   ![Erreur dans la fenêtre Liste d’erreurs](../ide/media/get-started-cpp-error-list.png "Erreur dans la fenêtre Liste d’erreurs")

   Dans votre code, il manque une déclaration pour [std::cout](/cpp/standard-library/iostream), qui se trouve dans le fichier d’en-tête \<iostream>.

1. Pour ajouter l’en-tête iostream, entrez ce code après `#include "stdafx.h"` :

   ```cpp
   #include <iostream>
   using namespace std;
   ```

   Vous avez sans doute remarqué qu’une zone est apparue quand vous avez commencé à entrer le code. Cette zone contient des suggestions de saisie semi-automatique pour les caractères que vous venez d’entrer. Il s’agit d’une option de la fonctionnalité IntelliSense C++, qui fournit des invites de codage, notamment des membres de classe ou d’interface et des informations sur les paramètres. Vous pouvez aussi utiliser des extraits de code, qui sont des blocs de code prédéfinis. Pour plus d’informations, consultez [Using IntelliSense](../ide/using-intellisense.md) et [Code Snippets](../ide/code-snippets.md).

   ![Code fixe dans l’éditeur](../ide/media/get-started-cpp-cout-fix.png "Code fixe dans l’éditeur")

   La ligne ondulée rouge sous `cout` disparaît lorsque vous corrigez l’erreur.

1. Pour enregistrer les modifications dans le fichier, appuyez sur **Ctrl+S**.

## <a name="build-the-app"></a>Générer l’application

Vous pouvez facilement générer votre code. Dans la barre de menus, choisissez **Générer > Générer la solution**. Visual Studio génère la solution HelloApp, tout en affichant l’avancement de l’opération dans la fenêtre **Sortie**.

   ![Générer la solution HelloApp](../ide/media/get-started-cpp-build-solution.gif "Générer la solution HelloApp")

## <a name="debug-and-test-the-app"></a>Déboguer et tester l’application

Vous pouvez déboguer HelloApp pour vérifier si le mot « Hello » s’affiche bien dans la fenêtre de console.

### <a name="to-debug-the-app"></a>Pour déboguer l'application

1. Pour démarrer le débogueur, choisissez **Déboguer > Démarrer le débogage** dans la barre de menus.

   ![Commande Démarrer le débogage dans le menu Déboguer](../ide/media/get-started-cpp-start-debugging-menu.png "Commande Démarrer le débogage dans le menu Déboguer")

   Le débogueur démarre et exécute le code. La fenêtre de console (une fenêtre distincte qui ressemble à une invite de commandes) s’affiche pendant quelques secondes, mais se clôt rapidement lorsque le débogueur s’arrête en cours d’exécution. Pour afficher le texte, vous devez définir un point d’arrêt afin d’interrompre l’exécution du programme.

### <a name="to-add-a-breakpoint"></a>Pour ajouter un point d’arrêt

1. Dans l’éditeur, placez le curseur dans la ligne `return 0;`. Dans la barre de menus, choisissez **Déboguer > Basculer le point d’arrêt**. Vous pouvez également cliquer dans la marge de gauche pour définir un point d’arrêt.

     ![Commande Basculer le point d’arrêt dans le menu Déboguer](../ide/media/get-started-cpp-toggle-breakpoint-menu.png "Commande Basculer le point d’arrêt dans le menu Déboguer")

     Un cercle rouge apparaît à côté de la ligne de code dans la bordure gauche de la fenêtre de l’éditeur.

     ![Point d’arrêt indiqué dans la marge de la fenêtre](../ide/media/get-started-cpp-breakpoint-set.png "Point d’arrêt indiqué dans la marge de la fenêtre")

1. Pour démarrer le débogage, appuyez sur **F5**.

   Le débogueur démarre et une fenêtre de console apparaît avec le mot **Hello**.

   ![Texte Hello dans la fenêtre de console](../ide/media/get-started-cpp-helloapp-window.png "Texte Hello dans la fenêtre de console")

1. Pour arrêter le débogage, appuyez sur **Maj+F5**.

Pour plus d’informations sur le débogage des projets console, consultez [Projets console](../debugger/debugging-preparation-console-projects.md).

## <a name="build-a-release-version-of-the-app"></a>Générer une version release de l’application

Maintenant que vous avez vérifié que tout fonctionne, vous pouvez préparer une version Release de l’application. Les versions de mise en production ne conservent pas les informations de débogage et utilisent des options d’optimisation du compilateur pour créer du code d’une taille plus petite et qui s’exécute plus vite.

### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Pour nettoyer les fichiers solution et générer une version Release

1. Dans la barre de menus, choisissez **Générer > Nettoyer la solution** pour supprimer les fichiers intermédiaires et les fichiers de sortie créés pendant les générations précédentes.

   ![Commande Nettoyer la solution du menu Générer](../ide/media/get-started-cpp-clean-solution-menu.png "ExploreIDE-CleanSolution")

1. Pour changer la configuration de la solution HelloApp de **Debug** à **Release**, dans la barre d’outils, sélectionnez la liste déroulante du contrôle Configurations de solutions, puis choisissez **Release**.

   ![Générer une version Release de l’application](../ide/media/get-started-cpp-set-release-configuration.png "C++IDE_ChangingBuildtoRelease")

1. Générez la solution. Dans la barre de menus, choisissez **Générer > Générer la solution**.

Quand cette génération est terminée, vous avez une nouvelle application prête à être copiée et exécutée dans une fenêtre d’invite de commandes. Cette application est très simple, mais il ne tient qu’à vous de créer des applications plus complexes.

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Pour explorer d’autres exemples, consultez [Visual Studio Samples](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de l’IDE de Visual Studio pour le développement de bureau C++](/cpp/ide/using-the-visual-studio-ide-for-cpp-desktop-development)  
[Procédure pas à pas : création d'une application simple avec C# ou Visual Basic](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md)  
[Conseils de productivité pour Visual Studio](../ide/productivity-tips-for-visual-studio.md)  
[Exemples Visual Studio](../ide/visual-studio-samples.md)  
[Bien démarrer avec le développement dans Visual Studio](../ide/get-started-developing-with-visual-studio.md)
