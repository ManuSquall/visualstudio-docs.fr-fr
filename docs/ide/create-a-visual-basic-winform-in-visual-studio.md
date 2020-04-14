---
title: Créer une application Windows Forms avec Visual Basic
description: Découvrez comment créer une application Windows Forms dans Visual Studio avec Visual Basic, étape par étape.
ms.date: 09/27/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 89effbfd31e0194a88067a340c9332d888ef23df
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224548"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Créer une application Windows Forms dans Visual Studio avec Visual Basic

Dans cette courte présentation de l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer une application Visual Basic simple qui comporte une interface utilisateur Windows.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

> [!NOTE]
> Certaines des captures d’écran de ce tutoriel utilisent le thème foncé. Si vous n’utilisez pas le thème foncé mais que vous aimeriez l’utiliser, consultez la page [Personnaliser l’éditeur et l’IDE de Visual Studio](../ide/quickstart-personalize-the-ide.md) pour savoir comment faire.

::: moniker-end

## <a name="create-a-project"></a>Création d’un projet

Tout d’abord, vous allez créer un projet d’application Visual Basic. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

1. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **Visual Basic**, puis choisissez **Bureau Windows**. Dans le volet central, choisissez **Windows Forms App (.NET Framework)**. Nommez ensuite le fichier `HelloWorld`.

     Si vous ne voyez pas le modèle de projet **Windows Forms App (.NET Framework)**, quittez la boîte de dialogue **Nouveau projet** puis, dans la barre de menus supérieure, choisissez **Outils** > **Obtenir les outils et fonctionnalités**. Visual Studio Installer est lancé. Choisissez la charge de travail **de développement de bureau .NET,** puis choisissez **Modifier**.

     ![Charge de travail .NET Core dans Visual Studio Installer](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Ouvrez Visual Studio 2019.

1. Sur la fenêtre de départ, choisissez **Créer un nouveau projet**.

   ![Afficher la fenêtre « Créer un projet »](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Sur la **fenêtre Créer un nouveau projet,** choisissez le modèle Windows Forms App **(.NET Framework)** pour Visual Basic.

   (Si vous préférez, vous pouvez affiner votre recherche pour accéder rapidement au modèle que vous voulez. Par exemple, entrez ou tapez *l’application formulaires Windows* dans la boîte de recherche. Ensuite, choisissez **Visual Basic** dans la liste de langue, puis choisissez **Windows** dans la liste de la plate-forme.)  

   ![Choisir le modèle Visual Basic pour l’application Windows Forms (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

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

   ![Dans la fenêtre « Configurer votre nouveau projet », nommez votre projet « HelloWorld »](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio ouvre votre nouveau projet.

::: moniker-end

## <a name="create-the-application"></a>Création de l'application

Une fois que vous avez sélectionné votre modèle de projet Visual Basic et nommé votre fichier, Visual Studio ouvre un formulaire. Un formulaire est une interface utilisateur Windows. Nous allons créer une application "Hello World" en ajoutant des contrôles sur le formulaire, puis nous allons exécuter l’application.

### <a name="add-a-button-to-the-form"></a>Ajouter un bouton au formulaire

1. Cliquez sur **Toolbox** pour ouvrir la fenêtre de sortie de la boîte à outils.

     ![Cliquer sur la boîte à outils pour ouvrir la fenêtre Boîte à outils](../ide/media/vb-toolbox-toolwindow.png)

     (Si vous ne voyez pas l’option de vol **Toolbox,** vous pouvez l’ouvrir à partir de la barre de menu. Pour ce faire, **Voir Toolbox** > **Toolbox**. Ou, appuyez sur **Ctrl**+**Alt**+**X**.)

1. Cliquez sur l’icône **Pin** pour amarrer la fenêtre de la boîte à **outils.**

     ![Cliquer sur l’icône Épingler pour épingler la fenêtre Boîte à outils à l’IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Cliquez sur le contrôle **Button**, puis faites-le glisser sur le formulaire.

     ![Ajouter un bouton au formulaire](../ide/media/vb-add-a-button-to-form1.png)

1. Dans la section **Apparence** (ou la section **Polices**) de la fenêtre **Propriétés**, tapez `Click this`, puis appuyez sur **Entrée**.

     ![Ajouter du texte au bouton du formulaire](../ide/media/vb-button-control-text.png)

     (Si vous ne voyez pas la fenêtre **Propriétés,** vous pouvez l’ouvrir à partir de la barre de menu. Pour ce faire, cliquez sur **View** > **Properties Window**. Ou, appuyez sur **F4**.)

1. Dans la section **Design** de la fenêtre **Propriétés**, remplacez le nom **Button1** par `btnClickThis`, puis appuyez sur **Entrée**.

     ![Ajouter une fonction au bouton du formulaire](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Si vous avez alphabétisé la liste dans la fenêtre **Propriétés,** **Button1** apparaît dans la section **(DataBindings),** à la place.

### <a name="add-a-label-to-the-form"></a>Ajouter une étiquette au formulaire

Maintenant que nous avons ajouté un contrôle bouton pour créer une action, nous allons ajouter un contrôle étiquette auquel envoyer le texte.

1. Sélectionnez le contrôle **d’étiquette** de la fenêtre de la **boîte à outils,** puis faites-le glisser sur le formulaire et **laissez-le** tomber sous le cliquez sur ce bouton.

1. Dans la section **Conception** ou la section **(DataBindings)** de la fenêtre `lblHelloWorld` **Propriétés,** changer le nom de **Label1** à , puis appuyez sur **Enter**.

### <a name="add-code-to-the-form"></a>Ajouter du code au formulaire

1. Dans la fenêtre **Form1.vb &#91;Design&#93;**, double-cliquez sur le bouton **Click this** pour ouvrir la fenêtre **Form1.vb**.

      (Vous pouvez également développer **Form1.vb** dans **Explorateur de solutions**, puis cliquer sur **Form1**.)

1. Dans la fenêtre **Form1.vb,** entre les lignes Sub `lblHelloWorld.Text = "Hello World!"` **privés** et End **Sub,** tapez ou entrez comme indiqué dans la capture d’écran suivante :

     ![Ajouter du code au formulaire](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Exécution de l'application

1. Cliquez sur le bouton **Démarrer** pour exécuter l’application.

     ![Cliquer sur Démarrer pour déboguer et exécuter l’application](../ide/media/vb-click-start-hello-world.png)

   Il se passe alors plusieurs choses. Dans l’IDE Visual Studio, la fenêtre **Diagnostics Tools** s’ouvrira, et une fenêtre **de sortie** s’ouvrira également. Mais en dehors de l’IDE, une boîte de dialogue **Form1** apparaît. Il comprendra votre **Cliquez sur ce** bouton et le texte qui dit **Label1**.

1. Cliquez sur le bouton **Click this** dans la boîte de dialogue **Form1**. Notez que le texte **Label1** change pour **Hello World!**.

    ![Boîte de dialogue Form1 contenant le texte Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Fermez la boîte de dialogue **Form1** pour arrêter d’exécuter l’application.

## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus, passez au tutoriel suivant :

> [!div class="nextstepaction"]
> [Tutorial: Créer un spectateur d’image](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Voir aussi

* [Plus de tutoriels de base visuelle](/visualstudio/get-started/visual-basic/)
* [Tutoriels C#](/visualstudio/get-started/csharp/)
* [Tutoriels CMD](/cpp/get-started/tutorial-console-cpp)
