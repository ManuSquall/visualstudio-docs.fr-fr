---
title: 'Créer une application Windows Forms avec C #'
description: Découvrez comment créer une application Windows Forms dans Visual Studio avec CMD, étape par étape.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 8c798640ea80900c633b5b7d0817cc278a772a51
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224535"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Créer une application Windows Forms dans Visual Studio avec C #

Dans cette courte introduction à l’environnement de développement intégré Visual Studio (IDE), vous créerez une application C simple qui dispose d’une interface utilisateur (UI) basée sur Windows.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

> [!NOTE]
> Certaines des captures d’écran de ce tutoriel utilisent le thème foncé. Si vous n’utilisez pas le thème foncé mais que vous aimeriez l’utiliser, consultez la page [Personnaliser l’éditeur et l’IDE de Visual Studio](../ide/quickstart-personalize-the-ide.md) pour savoir comment faire.

::: moniker-end

## <a name="create-a-project"></a>Création d’un projet

Vous allez d’abord créer un projet d’application C#. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans la boîte de dialogue **New Project** dans la vitre gauche, étendre Visual **C ,** puis choisir Windows **Desktop**. Dans le volet central, choisissez **Windows Forms App (.NET Framework)**. Nommez ensuite le fichier `HelloWorld`.

     Si vous ne voyez pas le modèle de projet **Windows Forms App (.NET Framework)**, quittez la boîte de dialogue **Nouveau projet** puis, dans la barre de menus supérieure, choisissez **Outils** > **Obtenir les outils et fonctionnalités**. Visual Studio Installer est lancé. Choisissez la charge de travail **de développement de bureau .NET,** puis choisissez **Modifier**.

     ![Charge de travail .NET Core dans Visual Studio Installer](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Ouvrez Visual Studio 2019.

1. Sur la fenêtre de départ, choisissez **Créer un nouveau projet**.

   ![Afficher la fenêtre « Créer un projet »](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Sur la **fenêtre Créer un nouveau projet,** choisissez le modèle Windows Forms App **(.NET Framework)** pour C.

   (Si vous préférez, vous pouvez affiner votre recherche pour accéder rapidement au modèle que vous voulez. Par exemple, entrez ou tapez *l’application formulaires Windows* dans la boîte de recherche. Ensuite, choisissez **C de** la liste linguistique, puis choisissez **Windows** dans la liste de la plate-forme.)  

   ![Choisissez le modèle C pour l’application formulaires Windows (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > Si vous ne voyez pas le modèle **Windows Forms (.NET Framework)**, vous pouvez l’installer à partir de la fenêtre **Créer un projet**. Dans le **Vous ne trouvez pas ce que vous cherchez ?**, choisissez le lien **Installer plus d’outils et de fonctionnalités**.
   >
   > ![Le lien « Installer plus d’outils et de fonctionnalités » du message « Vous ne trouvez pas ce que vous cherchez ? » dans la fenêtre « Créer un projet »](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Ensuite, dans Visual Studio Installer, choisissez la charge de travail **Développement .NET Desktop**.
   >
   > ![Charge de travail .NET Core dans Visual Studio Installer](../ide/media/install-dot-net-desktop-env.png)
   >
   > Après cela, choisissez le bouton **Modifier** dans Visual Studio Installer. Vous pouvez être invité à enregistrer votre travail ; le cas échéant, faites-le. Ensuite, choisissez **Continuer** pour installer la charge de travail. Ensuite, revenez à l’étape 2 de cette procédure « [Créer un projet](#create-a-project) ».

1. Dans la fenêtre **Configurer votre nouveau projet**, tapez ou entrez *HelloWorld* dans la zone **Nom du projet**. Ensuite, choisissez **Créer**.

   ![Dans la fenêtre « Configurer votre nouveau projet », nommez votre projet « HelloWorld »](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   Visual Studio ouvre votre nouveau projet.

::: moniker-end

## <a name="create-the-application"></a>Création de l'application

Après avoir sélectionné votre modèle de projet C et nommé votre fichier, Visual Studio vous ouvre un formulaire. Un formulaire est une interface utilisateur Windows. Nous allons créer une application "Hello World" en ajoutant des contrôles sur le formulaire, puis nous allons exécuter l’application.

### <a name="add-a-button-to-the-form"></a>Ajouter un bouton au formulaire

1. Choisissez **Boîte à outils** pour ouvrir la fenêtre volante Boîte à outils.

     ![Choisissez la boîte à outils pour ouvrir la fenêtre de la boîte à outils](../ide/media/csharp-toolbox-toolwindow.png)

     (Si vous ne voyez pas l’option de vol **Toolbox,** vous pouvez l’ouvrir à partir de la barre de menu. Pour ce faire, **Voir Toolbox** > **Toolbox**. Ou, appuyez sur **Ctrl**+**Alt**+**X**.)

1. Choisissez l’icône **Pin** pour amarrer la fenêtre **Toolbox.**

     ![Choisissez l’icône Pin pour épingler la fenêtre toolbox à l’IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Choisissez le contrôle **du bouton,** puis faites-le glisser sur le formulaire.

     ![Ajouter un bouton au formulaire](../ide/media/csharp-add-button-form1.png)

1. Dans la fenêtre **Propriétés,** localiser **le texte**, changer le nom de **Button1** à `Click this`, puis appuyez sur **Entrez**.

     ![Ajouter du texte au bouton du formulaire](../ide/media/vb-button-control-text.png)

     (Si vous ne voyez pas la fenêtre **Propriétés,** vous pouvez l’ouvrir à partir de la barre de menu. Pour ce faire, choisissez **View** > **Properties Window**. Ou, appuyez sur **F4**.)

1. Dans la section **Design** de la fenêtre **Propriétés**, remplacez le nom **Button1** par `btnClickThis`, puis appuyez sur **Entrée**.

     ![Ajouter une fonction au bouton du formulaire](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Si vous avez alphabétisé la liste dans la fenêtre **Propriétés,** **Button1** apparaît dans la section **(DataBindings),** à la place.

### <a name="add-a-label-to-the-form"></a>Ajouter une étiquette au formulaire

Maintenant que nous avons ajouté un contrôle bouton pour créer une action, nous allons ajouter un contrôle étiquette auquel envoyer le texte.

1. Sélectionnez le contrôle **d’étiquette** de la fenêtre de la **boîte à outils,** puis faites-le glisser sur le formulaire et **laissez-le** tomber sous le cliquez sur ce bouton.

1. Dans la section **Conception** ou la section **(DataBindings)** de la fenêtre `lblHelloWorld` **Propriétés,** changer le nom de **Label1** à , puis appuyez sur **Enter**.

### <a name="add-code-to-the-form"></a>Ajouter du code au formulaire

1. Dans la **Form1.cs fenêtre &#91;&#91;design&#93;&#91;,** cliquez deux fois sur **ce** bouton pour ouvrir la fenêtre **Form1.cs.**

      (Alternativement, vous pouvez étendre **Form1.cs** dans **Solution Explorer**, puis choisir **Form1**.)

1. Dans la fenêtre **Form1.cs,** après la ligne vide `lblHelloWorld.Text = "Hello World!";` **privée,** tapez ou entrez comme indiqué dans la capture d’écran suivante :

     ![Ajouter du code au formulaire](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Exécution de l'application

1. Choisissez le bouton **Démarrer** pour exécuter l’application.

     ![Choisissez Start to debug et exécutez l’application](../ide/media/vb-click-start-hello-world.png)

   Il se passe alors plusieurs choses. Dans l’IDE Visual Studio, la fenêtre **Diagnostics Tools** s’ouvrira, et une fenêtre **de sortie** s’ouvrira également. Mais en dehors de l’IDE, une boîte de dialogue **Form1** apparaît. Il comprendra votre **Cliquez sur ce** bouton et le texte qui dit **Label1**.

1. Choisissez le **Cliquez sur ce** bouton dans la boîte de dialogue **Form1.** Notez que le texte **Label1** change pour **Hello World!**.

    ![Boîte de dialogue Form1 contenant le texte Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Fermez la boîte de dialogue **Form1** pour arrêter d’exécuter l’application.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus, passez au tutoriel suivant :

> [!div class="nextstepaction"]
> [Tutorial: Créer un spectateur d’image](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Voir aussi

* [Plus de tutoriels C](/visualstudio/get-started/csharp/)
* [Tutoriels Visual Basic](/visualstudio/get-started/visual-basic/)
* [Tutoriels CMD](/cpp/get-started/tutorial-console-cpp)
