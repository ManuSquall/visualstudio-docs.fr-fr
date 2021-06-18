---
title: Utiliser Visual Studio pour créer une première application console C#
titleSuffix: ''
description: Découvrez pas à pas comment créer une application console Hello World simple dans Visual Studio, en C#.
ms.custom: acquisition, seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 21cab6f8fd8f4ff6a86a780774d031e60b03e780
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307997"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Démarrage rapide : Utiliser Visual Studio pour créer une première application console C#

Dans cette présentation de 5-10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer une application C# simple qui s’exécute dans la console.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2022"

Si vous n’avez pas encore installé Visual Studio 2022 Preview, accédez à la page [téléchargements Visual studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) pour l’installer gratuitement.

::: moniker-end

## <a name="create-a-project"></a>Création d’un projet

Vous allez d’abord créer un projet d’application C#. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **fichier** > **nouveau** > **projet**.

3. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **C#**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application console (.NET Core)**. Ensuite, nommez le projet *HelloWorld*.

   ![Modèle de projet d’application console (.NET Core) dans la boîte de dialogue Nouveau projet dans l’IDE de Visual Studio](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Si vous ne voyez pas le modèle de projet **Application console (.NET Core)**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**.

   ![Cliquer sur le lien Ouvrir Visual Studio Installer dans la boîte de dialogue Nouveau projet](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

     ![Charge de travail Développement multiplateforme .Net Core dans le programme d’installation de Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Ouvrez Visual Studio.

1. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

   ![Fenêtre « Créer un projet »](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Dans la fenêtre **Créer un projet**, entrez ou tapez *console* dans la zone de recherche. Ensuite, choisissez **C#** Dans la liste des langages, puis choisissez **Windows** dans la liste des plateformes. 

   Après avoir appliqué les filtres de langage et de plateforme, choisissez le modèle **Application console (.NET Core)**, puis choisissez **Suivant**.

   ![Choisissez le modèle C# pour l’application console (.NET Framework).](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Si vous ne voyez pas le modèle **Application console (.NET Core)**, vous pouvez l’installer à partir de la fenêtre **Créer un projet**. Dans le **Vous ne trouvez pas ce que vous cherchez ?**, choisissez le lien **Installer plus d’outils et de fonctionnalités**.
   >
   > ![Le lien « Installer plus d’outils et de fonctionnalités » du message « Vous ne trouvez pas ce que vous cherchez ? » dans la fenêtre « Créer un projet »](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ensuite, dans Visual Studio Installer, choisissez la charge de travail **Développement multiplateforme .NET Core**.
   >
   > ![Charge de travail Développement multiplateforme .Net Core dans le programme d’installation de Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Après cela, choisissez le bouton **Modifier** dans Visual Studio Installer. Vous pouvez être invité à enregistrer votre travail ; le cas échéant, faites-le. Ensuite, choisissez **Continuer** pour installer la charge de travail. Ensuite, revenez à l’étape 2 de cette procédure « [Créer un projet](#create-a-project) ».

1. Dans la fenêtre **Configurer votre nouveau projet**, tapez ou entrez *HelloWorld* dans la zone **Nom du projet**. Ensuite, choisissez **créer**.

   ![Dans la fenêtre « Configurer votre nouveau projet », nommez votre projet « HelloWorld »](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio ouvre votre nouveau projet.
   
::: moniker-end

## <a name="create-the-application"></a>Création de l'application

::: moniker range="vs-2017"

Une fois que vous avez sélectionné votre modèle de projet C# et nommé votre projet, Visual Studio crée une application « Hello World » simple.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio inclut le code de « Hello World » par défaut dans votre projet.

::: moniker-end

(Pour cela, il appelle la méthode <xref:System.Console.WriteLine%2A> pour d’afficher la chaîne littérale « Hello World! » dans la fenêtre de console.)

   ![Afficher le code Hello World par défaut à partir du modèle](../ide/media/csharp-console-helloworld-template.png)

Si vous appuyez sur **F5**, le programme s’exécute en mode débogage. Cependant, la fenêtre de console ne reste visible qu’un instant avant de se fermer.

(Ce comportement se produit car la méthode `Main` se termine après l’exécution de sa seule instruction, entraînant la fin de l’application.)

### <a name="add-some-code"></a>Ajouter du code

Nous allons ajouter du code pour suspendre l’application afin que la fenêtre de console ne se ferme pas tant que vous n’avez pas appuyé sur **Entrée**.

1. Ajoutez le code suivant immédiatement après l’appel à la méthode <xref:System.Console.WriteLine%2A> :

   ```csharp
   Console.ReadLine();
   ```

1. Vérifiez qu’elle se présente ainsi dans l’éditeur de code :

   ![Ajouter du code pour suspendre l’application Hello World](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Exécution de l'application

1. Cliquez sur le bouton **HelloWorld** dans la barre d’outils pour exécuter l’application en mode débogage. (Ou, vous pouvez appuyer sur **F5**.)

   ![Cliquer sur le bouton Hello World pour exécuter l’application à partir de la barre d’outils](../ide/media/csharp-console-hello-world-button.png)

1. Votre application s’affiche dans la fenêtre de console.

   ![Fenêtre de console affichant Hello World!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Fermer l'application

1. Appuyez sur **Entrée** pour fermer la fenêtre de console.

1. Fermez le volet de **sortie** dans Visual Studio.

   ![Fermer le volet Sortie dans Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Fermez Visual Studio.

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous avez appris des choses sur C# et l’environnement IDE de Visual Studio. Pour plus d’informations, passez aux tutoriels suivants.

> [!div class="nextstepaction"]
> [Bien démarrer avec une application console C# dans Visual Studio](../get-started/csharp/tutorial-console.md)
