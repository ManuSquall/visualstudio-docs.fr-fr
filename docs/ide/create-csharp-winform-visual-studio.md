---
title: Créer une application Windows Forms avecC#
description: Découvrez comment créer une application Windows Forms dans Visual Studio avec C#, pas à pas.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 4017ee2da040ccef36c58b17d896abab199c3517
ms.sourcegitcommit: 13decf878b33fc0c5d665a88067170c2861b261b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71682143"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Créer une application Windows Forms dans Visual Studio avecC#

Dans cette brève introduction à l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer C# une application simple dotée d’une interface utilisateur Windows.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

> [!NOTE]
> Certaines des captures d’écran de ce tutoriel utilisent le thème foncé. Si vous n’utilisez pas le thème foncé, mais que vous aimeriez l’utiliser, consultez la page [Personnaliser l’éditeur et l’IDE de Visual Studio](../ide/quickstart-personalize-the-ide.md) pour savoir comment faire.

::: moniker-end

## <a name="create-a-project"></a>Créer un projet

Vous allez d’abord créer un projet d’application C#. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans la boîte de dialogue **nouveau projet** , dans le volet gauche, développez **C#visuel**, puis choisissez **Bureau Windows**. Dans le volet central, choisissez **Windows Forms App (.NET Framework)** . Nommez ensuite le fichier `HelloWorld`.

     Si vous ne voyez pas le modèle de projet **Windows Forms App (.NET Framework)** , quittez la boîte de dialogue **Nouveau projet** puis, dans la barre de menus supérieure, choisissez **Outils** > **Obtenir les outils et fonctionnalités**. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement .NET Desktop**, puis choisissez **Modifier**.

     ![Charge de travail .NET Core dans Visual Studio Installer](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Ouvrez Visual Studio 2019.

1. Dans la fenêtre de démarrage, choisissez **Créer un projet**.

   ![Afficher la fenêtre « Créer un projet »](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Dans la fenêtre **créer un nouveau projet** , choisissez le modèle d' **application Windows Forms (.NET Framework)** pour C#.

   (Si vous préférez, vous pouvez affiner votre recherche pour accéder rapidement au modèle de votre choix. Par exemple, entrez ou tapez *Windows Forms application* dans la zone de recherche. Ensuite, choisissez **C#** dans la liste langue, puis choisissez **Windows** dans la liste plateforme.)  

   ![Choisir le C# modèle pour l’application Windows Forms (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > Si vous ne voyez pas le modèle **Windows Forms (.NET Framework)** , vous pouvez l’installer à partir de la fenêtre **Créer un projet**. Dans le **Vous ne trouvez pas ce que vous cherchez ?** , choisissez le lien **Installer plus d’outils et de fonctionnalités**.
   >
   > ![Le lien « Installer plus d’outils et de fonctionnalités » du message « Vous ne trouvez pas ce que vous cherchez ? » dans la fenêtre « Créer un projet »](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ensuite, dans Visual Studio Installer, choisissez la charge de travail **Développement .NET Desktop**.
   >
   > ![Charge de travail .NET Core dans Visual Studio Installer](../ide/media/install-dot-net-desktop-env.png)
   >
   > Après cela, choisissez le bouton **Modifier** dans Visual Studio Installer. Vous pouvez être invité à enregistrer votre travail ; le cas échéant, faites-le. Ensuite, choisissez **Continuer** pour installer la charge de travail. Ensuite, revenez à l’étape 2 de cette procédure « [Créer un projet](#create-a-project) ».

1. Dans la fenêtre **Configurer votre nouveau projet**, tapez ou entrez *HelloWorld* dans la zone **Nom du projet**. Choisissez ensuite **Créer**.

   ![Dans la fenêtre « Configurer votre nouveau projet », nommez votre projet « HelloWorld »](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio ouvre votre nouveau projet.

::: moniker-end

## <a name="create-the-application"></a>Créer l’application

Une fois que vous C# avez sélectionné votre modèle de projet et que vous avez nommé votre fichier, Visual Studio ouvre un formulaire pour vous. Un formulaire est une interface utilisateur Windows. Nous allons créer une application « Hello World » en ajoutant des contrôles au formulaire, puis exécuter l’application.

### <a name="add-a-button-to-the-form"></a>Ajouter un bouton au formulaire

1. Choisissez **Boîte à outils** pour ouvrir la fenêtre volante Boîte à outils.

     ![Choisissez la boîte à outils pour ouvrir la fenêtre boîte à outils](../ide/media/csharp-toolbox-toolwindow.png)

     (Si vous ne voyez pas la fenêtre volante **Boîte à outils**, ouvrez-la à partir de la barre de menus. Pour ce faire, **Affichez**la**boîte à outils** > . Vous pouvez aussi appuyer sur **Ctrl**+**Alt**+**X**.)

1. Choisissez l’icône **épingler** pour ancrer la fenêtre **boîte à outils** .

     ![Choisissez l’icône d’épingle pour épingler la fenêtre boîte à outils à l’IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Choisissez le contrôle **Button** , puis faites-le glisser sur le formulaire.

     ![Ajouter un bouton au formulaire](../ide/media/csharp-add-button-form1.png)

1. Dans la fenêtre **Propriétés** , recherchez **Text**, changez le nom de **Button1** en `Click this`, puis appuyez sur **entrée**.

     ![Ajouter du texte au bouton du formulaire](../ide/media/vb-button-control-text.png)

     (Si vous ne voyez pas la fenêtre **Propriétés**, ouvrez-la à partir de la barre de menus. Pour ce faire, choisissez **afficher** > **fenêtre Propriétés**. Vous pouvez aussi appuyer sur **F4**.)

1. Dans la section **Design** de la fenêtre **Propriétés**, remplacez le nom **Button1** par `btnClickThis`, puis appuyez sur **Entrée**.

     ![Ajouter une fonction au bouton du formulaire](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Si vous avez classé par ordre alphabétique la liste dans la fenêtre **Propriétés** , **Button1** apparaît dans la section **(DataBindings)** à la place.

### <a name="add-a-label-to-the-form"></a>Ajouter une étiquette au formulaire

Maintenant que nous avons ajouté un contrôle bouton pour créer une action, nous allons ajouter un contrôle étiquette auquel envoyer le texte.

1. Sélectionnez le contrôle **Label** dans la fenêtre **Boîte à outils**, puis faites-le glisser sur le formulaire en dessous du bouton **Click this**.

1. Dans la section **conception** ou la section **(DataBindings)** de la fenêtre **Propriétés** , remplacez le nom de **Label1** par `lblHelloWorld`, puis appuyez sur **entrée**.

### <a name="add-code-to-the-form"></a>Ajouter du code au formulaire

1. Dans la **fenêtre &#91;de&#93; conception de Form1.cs** , double-cliquez sur le bouton **cliquez sur ce** bouton pour ouvrir la fenêtre **Form1.cs** .

      (Vous pouvez également développer **Form1.cs** dans **Explorateur de solutions**, puis choisir **Form1**.)

1. Dans la fenêtre **Form1.cs** , après la ligne **private void** , tapez ou entrez `lblHelloWorld.Text = "Hello World!";` comme indiqué dans la capture d’écran suivante :

     ![Ajouter du code au formulaire](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Exécuter l'application

1. Choisissez le bouton **Démarrer** pour exécuter l’application.

     ![Choisissez Démarrer pour déboguer et exécuter l’application](../ide/media/vb-click-start-hello-world.png)

   Il se passe alors plusieurs choses. Dans l’IDE de Visual Studio, la fenêtre **Outils de diagnostic** et une fenêtre **Sortie** s’ouvrent. En dehors de l’IDE, une boîte de dialogue **Form1** s’affiche. Elle contient le bouton **Click this** et le texte **Label1**.

1. **Cliquez sur ce** bouton dans la boîte de dialogue **Form1** . Notez que le texte **Label1** devient **Hello World !** .

    ![Boîte de dialogue Form1 contenant le texte Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Fermez la boîte de dialogue **Form1** pour arrêter l’exécution de l’application.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus, passez au tutoriel suivant :

> [!div class="nextstepaction"]
> [Tutoriel : Créer une visionneuse d’images @ no__t-0

## <a name="see-also"></a>Voir aussi

* [Autres C# didacticiels](/visualstudio/get-started/csharp/)
* [Didacticiels de Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++gratuits](/cpp/get-started/tutorial-console-cpp)
