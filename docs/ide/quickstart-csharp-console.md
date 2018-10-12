---
title: 'Démarrage rapide : Utiliser Visual Studio pour créer une première application console C#'
description: Découvrez pas à pas comment créer une application console Hello World simple dans Visual Studio, en C#.
ms.custom: ''
ms.date: 09/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 2766af365625890a0769f298d1801179da9c7e07
ms.sourcegitcommit: 25fc9605ba673afb51a24ce587cf4304b06aa577
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47029311"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Démarrage rapide : Utiliser Visual Studio pour créer une première application console C#

Dans cette présentation de 5-10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer une application C# simple qui s’exécute dans la console.

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

## <a name="create-a-project"></a>Créer un projet

Vous allez d’abord créer un projet d’application C#. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

3. Dans le volet gauche de la boîte de dialogue **Nouveau projet**, développez **C#**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application console (.NET Core)**. Ensuite, nommez le projet *HelloWorld*.

   ![Modèle de projet d’application console (.NET Core) dans la boîte de dialogue Nouveau projet dans l’IDE de Visual Studio](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Si vous ne voyez pas le modèle de projet **Application console (.NET Core)**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**.

   ![Cliquer sur le lien Ouvrir Visual Studio Installer dans la boîte de dialogue Nouveau projet](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

     ![Charge de travail Développement multiplateforme .Net Core dans Visual Studio Installer](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>Créer l’application

Une fois que vous avez sélectionné votre modèle de projet C# et nommé votre projet, Visual Studio crée une application « Hello World » simple. 

(Pour cela, il appelle la méthode <xref:System.Console.WriteLine%2A> afin d’afficher la chaîne littérale « Hello World! » dans la fenêtre de console.)

   ![Afficher le code Hello World par défaut à partir du modèle](../ide/media/csharp-console-helloworld-template.png)

Si vous appuyez sur **F5**, le programme s’exécute en mode débogage. Cependant, la fenêtre de console ne reste visible qu’un instant avant de se fermer.

(Cela s’explique par le fait que la méthode `Main` se termine après l’exécution de son instruction unique, entraînant la fin de l’application.)

### <a name="add-some-code"></a>Ajouter du code

Nous allons ajouter du code pour suspendre l’application afin que la fenêtre de console ne se ferme pas tant que vous n’avez pas appuyé sur **Entrée**.

1. Ajoutez le code suivant immédiatement après l’appel à la méthode <xref:System.Console.WriteLine%2A> :

   ```csharp
   Console.ReadLine();
   ```

1. Vérifiez qu’elle se présente ainsi dans l’éditeur de code :

   ![Ajouter du code pour suspendre l’application Hello World](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Exécuter l'application

1. Cliquez sur le bouton **HelloWorld** dans la barre d’outils pour exécuter l’application en mode débogage. (Vous pouvez également appuyer sur **F5**.)

   ![Cliquer sur le bouton Hello World pour exécuter le programme à partir de la barre d’outils](../ide/media/csharp-console-hello-world-button.png)

1. Votre application s’affiche dans la fenêtre de console.

   ![Fenêtre de console affichant Hello World!](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Fermer l'application

1. Appuyez sur **Entrée** pour fermer la fenêtre de console.

1. Fermez le volet **Sortie** dans Visual Studio.

   ![Fermer le volet Sortie dans Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Fermez Visual Studio.

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous avez appris des choses sur C# et l’environnement IDE de Visual Studio. Pour plus d’informations, passez aux tutoriels suivants.

> [!div class="nextstepaction"]
> [Tutoriels C#](/dotnet/csharp/tutorials/)
