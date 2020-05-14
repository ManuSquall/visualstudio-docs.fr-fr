---
title: Créer votre première application console avec Visual Basic
description: Découvrez comment créer une simple application console Hello World dans Visual Studio, en Visual Basic, pas à pas.
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 34f3dc8642e2cf8e965e2ad303bed79931d2645c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579501"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Démarrage rapide : Créer votre première application console dans Visual Studio avec Visual Basic

Dans cette présentation de 5-10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer une application Visual Basic simple qui s’exécute dans la console.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

## <a name="create-a-project"></a>Création d’un projet

Tout d’abord, vous allez créer un projet d’application Visual Basic. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

3. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **Visual Basic**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application console (.NET Core)**. Ensuite, nommez le projet *HelloWorld*.

   ![Modèle de projet d’application console (.NET Core) dans la boîte de dialogue Nouveau projet dans l’IDE de Visual Studio](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Si vous ne voyez pas le modèle de projet **Application console (.NET Core)**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**.

   ![Cliquer sur le lien Ouvrir Visual Studio Installer dans la boîte de dialogue Nouveau projet](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

     ![Charge de travail Développement multiplateforme .Net Core dans le programme d’installation de Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Certaines des captures d’écran de ce guide de démarrage rapide utilisent le thème foncé. Si vous n’utilisez pas le thème foncé mais que vous aimeriez l’utiliser, consultez la page [Personnaliser l’éditeur et l’IDE de Visual Studio](quickstart-personalize-the-ide.md) pour savoir comment faire.

1. Ouvrez Visual Studio 2019.

1. Sur la fenêtre de départ, choisissez **Créer un nouveau projet**.

   ![Afficher la fenêtre « Créer un projet »](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Dans la fenêtre **Créer un projet**, entrez ou tapez *console* dans la zone de recherche. Ensuite, choisissez **Visual Basic** dans la liste des langages, puis choisissez **Windows** dans la liste des plateformes. 

   Après avoir appliqué les filtres de langage et de plateforme, choisissez le modèle **Application console (.NET Core)**, puis choisissez **Suivant**.

   ![Choisir le modèle Visual Basic pour l’application console (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Si vous ne voyez pas le modèle **Application console (.NET Core)**, vous pouvez l’installer à partir de la fenêtre **Créer un projet**. Dans le **Vous ne trouvez pas ce que vous cherchez ?**, choisissez le lien **Installer plus d’outils et de fonctionnalités**.
   >
   > ![Le lien « Installer plus d’outils et de fonctionnalités » du message « Vous ne trouvez pas ce que vous cherchez ? » dans la fenêtre « Créer un projet »](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ensuite, dans Visual Studio Installer, choisissez la charge de travail **Développement multiplateforme .NET Core**.
   >
   > ![Charge de travail Développement multiplateforme .Net Core dans le programme d’installation de Visual Studio](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Après cela, choisissez le bouton **Modifier** dans Visual Studio Installer. Vous pouvez être invité à enregistrer votre travail ; le cas échéant, faites-le. Ensuite, choisissez **Continuer** pour installer la charge de travail. Ensuite, revenez à l’étape 2 de cette procédure « [Créer un projet](#create-a-project) ».

1. Dans la fenêtre **Configurer votre nouveau projet**, tapez ou entrez *WhatIsYourName* dans la zone **Nom du projet**. Ensuite, choisissez **Créer**.

   ![Dans la fenêtre « Configurer votre nouveau projet », nommez votre projet « WhatIsYourName »](../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio ouvre votre nouveau projet.

::: moniker-end

## <a name="create-the-application"></a>Création de l'application

Une fois que vous avez sélectionné votre modèle de projet Visual Basic et nommé votre projet, Visual Studio crée une application « Hello World » simple. Il appelle la méthode <xref:System.Console.WriteLine%2A> pour afficher la chaîne littérale « Hello World ! » dans la fenêtre de console.

![Afficher le code Hello World par défaut à partir du modèle](../ide/media/vb-console-helloworld-template.png)

Si vous cliquez sur le bouton **HelloWorld** dans l’IDE, vous exécutez le programme en mode débogage.

  ![Cliquer sur le bouton Hello World pour exécuter le programme en mode débogage](../ide/media/vb-console-hello-world-button.png)

Dans ce cas, la fenêtre de console reste visible seulement un instant avant sa fermeture. Cela s’explique par le fait que la méthode `Main` se termine après l’exécution de son instruction unique, entraînant la fin de l’application.

### <a name="add-some-code"></a>Ajouter du code

Vous allez maintenant ajouter du code pour suspendre l’application et demander une entrée utilisateur.

1. Ajoutez le code suivant immédiatement après l’appel à la méthode <xref:System.Console.WriteLine%2A> :

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

    Le programme est alors suspendu jusqu’à ce que l’utilisateur appuie sur une touche.

2. Sur la barre de menu, sélectionnez **Build** > **Build Solution**.

   Ceci compile votre programme en un langage intermédiaire, qui est ensuite converti en code binaire par un compilateur juste-à-temps (JIT).

## <a name="run-the-application"></a>Exécuter l’application

1. Cliquez sur le bouton **HelloWorld** dans la barre d’outils.

   ![Cliquer sur le bouton Hello World pour exécuter le programme à partir de la barre d’outils](../ide/media/vb-console-hello-world-button.png)

2. Appuyez sur une touche pour fermer la fenêtre de console.

   ![Fenêtre de console affichant « Hello World » et « Press any key to continue »](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous en avez appris un peu plus sur Visual Basic et l’IDE de Visual Studio. Pour en apprendre davantage, passez au tutoriel suivant.

> [!div class="nextstepaction"]
> [Bien démarrer avec Visual Basic dans Visual Studio](../get-started/visual-basic/tutorial-console.md)
