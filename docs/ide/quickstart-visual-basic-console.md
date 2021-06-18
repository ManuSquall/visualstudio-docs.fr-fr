---
title: Créer votre première application console avec Visual Basic
description: Découvrez comment créer une simple application console Hello World dans Visual Studio, en Visual Basic, pas à pas.
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
- vb
ms.workload:
- multiple
ms.openlocfilehash: 7272e02ebfba084bdbe311d10b69d7b41fade0e1
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307906"
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Démarrage rapide : Créer votre première application console dans Visual Studio avec Visual Basic

Dans cette présentation de 5-10 minutes de l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer une application Visual Basic simple qui s’exécute dans la console.

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

Tout d’abord, vous allez créer un projet d’application Visual Basic. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **fichier** > **nouveau** > **projet**.

3. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **Visual Basic**, puis choisissez **.NET Core**. Dans le volet central, choisissez **Application console (.NET Core)**. Ensuite, nommez le projet *HelloWorld*.

   ![Modèle de projet d’application console (.NET Core) dans la boîte de dialogue Nouveau projet dans l’IDE de Visual Studio](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Si vous ne voyez pas le modèle de projet **Application console (.NET Core)**, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**.

   ![Cliquer sur le lien Ouvrir Visual Studio Installer dans la boîte de dialogue Nouveau projet](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Visual Studio Installer est lancé. Choisissez la charge de travail **Développement multiplateforme .NET Core**, puis choisissez **Modifier**.

     ![Charge de travail Développement multiplateforme .Net Core dans le programme d’installation de Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range=">=vs-2019"

> [!NOTE]
> Certaines des captures d’écran de ce guide de démarrage rapide utilisent le thème foncé. Si vous n’utilisez pas le thème foncé mais que vous aimeriez l’utiliser, consultez la page [Personnaliser l’éditeur et l’IDE de Visual Studio](quickstart-personalize-the-ide.md) pour savoir comment faire.

1. Ouvrez Visual Studio.

1. Dans la fenêtre Démarrer, choisissez **créer un nouveau projet**.

   ![Afficher la fenêtre « Créer un projet »](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Dans la fenêtre **créer un nouveau projet** , choisissez **Visual Basic** dans la liste langue. Ensuite, choisissez **Windows** dans la liste des plateformes et dans la **console** de la liste types de projets.

   Après avoir appliqué les filtres de langue, de plateforme et de type de projet, choisissez le modèle **application console** , puis cliquez sur **suivant**.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-create-new-project-console-net-core.png" alt-text="Choisir le modèle de Visual Basic pour l’application console":::

   > [!NOTE]
   > Si vous ne voyez pas le modèle **application console** , vous pouvez l’installer à partir de la fenêtre **créer un nouveau projet** . Dans le **Vous ne trouvez pas ce que vous cherchez ?**, choisissez le lien **Installer plus d’outils et de fonctionnalités**.
   >
   > ![Le lien « Installer plus d’outils et de fonctionnalités » du message « Vous ne trouvez pas ce que vous cherchez ? » dans la fenêtre « Créer un projet »](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Ensuite, dans Visual Studio Installer, choisissez la charge de travail **Développement multiplateforme .NET Core**.
   >
   > ![Charge de travail Développement multiplateforme .Net Core dans le programme d’installation de Visual Studio](../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Après cela, choisissez le bouton **Modifier** dans Visual Studio Installer. Vous pouvez être invité à enregistrer votre travail ; le cas échéant, faites-le. Ensuite, choisissez **Continuer** pour installer la charge de travail. Ensuite, revenez à l’étape 2 de cette procédure « [Créer un projet](#create-a-project) ».

1. Dans la fenêtre **Configurer votre nouveau projet**, tapez ou entrez *WhatIsYourName* dans la zone **Nom du projet**. Ensuite, choisissez **suivant**.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-name-your-project-whatname.png" alt-text="Dans la fenêtre « Configurer votre nouveau projet », nommez votre projet « WhatIsYourName »":::

1. Dans la fenêtre **informations supplémentaires** , **.net Core 3,1** doit déjà être sélectionné pour votre version cible de .NET Framework. Si ce n’est pas le cas, sélectionnez **.net Core 3,1**. Ensuite, choisissez **créer**.

   :::image type="content" source="../get-started/visual-basic/media/vs-2019/vb-target-framework.png" alt-text="Dans la fenêtre « informations supplémentaires », vérifiez que .NET Core 3,1 est sélectionné":::

   Visual Studio ouvre votre nouveau projet.

::: moniker-end

## <a name="create-the-application"></a>Création de l'application

Une fois que vous avez sélectionné votre modèle de projet Visual Basic et nommé votre projet, Visual Studio crée une application « Hello World » simple. Il appelle la méthode <xref:System.Console.WriteLine%2A> pour afficher la chaîne littérale « Hello World ! » dans la fenêtre de console.

![Afficher le code Hello World par défaut à partir du modèle](../ide/media/vb-console-helloworld-template.png)

Si vous cliquez sur le bouton **HelloWorld** dans l’IDE, vous exécutez le programme en mode débogage.

  ![Cliquer sur le bouton Hello World pour exécuter le programme en mode débogage](../ide/media/vb-console-hello-world-button.png)

Dans ce cas, la fenêtre de console reste visible seulement un instant avant sa fermeture. Cela s’explique par le fait que la méthode `Main` se termine après l’exécution de son instruction unique, entraînant la fin de l’application.

### <a name="add-some-code&quot;></a>Ajouter du code

Vous allez maintenant ajouter du code pour suspendre l’application et demander une entrée utilisateur.

1. Ajoutez le code suivant immédiatement après l’appel à la méthode <xref:System.Console.WriteLine%2A> :

   ```vb
   Console.Write(&quot;Press any key to continue...")
   Console.ReadKey(true)
   ```

    Le programme est alors suspendu jusqu’à ce que l’utilisateur appuie sur une touche.

2. Dans la barre de menus, sélectionnez **générer**  >  **générer la solution**.

   Ceci compile votre programme en un langage intermédiaire, qui est ensuite converti en code binaire par un compilateur juste-à-temps (JIT).

## <a name="run-the-application"></a>Exécution de l'application

1. Cliquez sur le bouton **HelloWorld** dans la barre d’outils.

   ![Cliquer sur le bouton Hello World pour exécuter le programme à partir de la barre d’outils](../ide/media/vb-console-hello-world-button.png)

2. Appuyez sur une touche pour fermer la fenêtre de console.

   ![Fenêtre de console affichant « Hello World » et « Press any key to continue »](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous en avez appris un peu plus sur Visual Basic et l’IDE de Visual Studio. Pour en apprendre davantage, passez au tutoriel suivant.

> [!div class="nextstepaction"]
> [Bien démarrer avec Visual Basic dans Visual Studio](../get-started/visual-basic/tutorial-console.md)
