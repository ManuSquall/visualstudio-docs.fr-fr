---
title: Créer une application Windows Forms avec Visual Basic
description: Découvrez comment créer une application Windows Forms dans Visual Studio avec Visual Basic, étape par étape.
ms.date: 03/23/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: c031a047a0331eea0f8397a303d2b5cb0af650e6
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180134"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Créer une application Windows Forms dans Visual Studio avec Visual Basic

Dans cette courte présentation de l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer une application Visual Basic simple qui comporte une interface utilisateur Windows.

::: moniker range="vs-2017"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) pour l’installer gratuitement.

::: moniker-end

::: moniker range="vs-2019"

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads) pour l’installer gratuitement.

> [!NOTE]
> Certaines des captures d’écran de ce tutoriel utilisent le thème foncé. Si vous n’utilisez pas le thème foncé, mais que vous aimeriez l’utiliser, consultez la page [Personnaliser l’éditeur et l’IDE de Visual Studio](../ide/quickstart-personalize-the-ide.md) pour savoir comment faire.

::: moniker-end

## <a name="create-a-project"></a>Créer un projet

Tout d’abord, vous allez créer un projet d’application Visual Basic. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

::: moniker range="vs-2017"

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

3. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **Visual Basic**, puis choisissez **Bureau Windows**. Dans le volet central, choisissez **Windows Forms App (.NET Framework)** . Nommez ensuite le fichier `HelloWorld`.

     Si vous ne voyez pas le modèle de projet **Windows Forms App (.NET Framework)** , quittez la boîte de dialogue **Nouveau projet** puis, dans la barre de menus supérieure, choisissez **Outils** > **Obtenir les outils et fonctionnalités**. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement .NET Desktop**, puis choisissez **Modifier**.

     ![Charge de travail .NET Core dans Visual Studio Installer](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Ouvrez Visual Studio 2019.

1. Dans la fenêtre de démarrage, choisissez **Créer un projet**.

   ![Afficher la fenêtre « Créer un projet »](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Dans la fenêtre **Créer un projet**, entrez ou tapez *Windows Forms* dans la zone de recherche. Ensuite, choisissez **Visual Basic** dans la liste des langages, puis choisissez **Windows** dans la liste des plateformes. 

   Après avoir appliqué les filtres de langage et de plateforme, choisissez le modèle **Application Windows Forms (.NET Framework)** , puis choisissez **Suivant**.

   ![Choisir le modèle Visual Basic pour l’application Windows Forms (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

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

   ![Dans la fenêtre « Configurer votre nouveau projet », nommez votre projet « HelloWorld »](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   Visual Studio ouvre votre nouveau projet.

::: moniker-end

## <a name="create-the-application"></a>Créer l’application

Une fois que vous avez sélectionné votre modèle de projet Visual Basic et nommé votre fichier, Visual Studio ouvre un formulaire. Un formulaire est une interface utilisateur Windows. Nous allons créer une application « Hello World » en ajoutant des contrôles au formulaire, puis exécuter cette application.

### <a name="add-a-button-to-the-form"></a>Ajouter un bouton au formulaire

1. Cliquez sur **Boîte à outils** pour ouvrir la fenêtre volante Boîte à outils.

     ![Cliquer sur la boîte à outils pour ouvrir la fenêtre Boîte à outils](../ide/media/vb-toolbox-toolwindow.png)

     (Si vous ne voyez pas la fenêtre volante **Boîte à outils**, vous pouvez l’ouvrir en appuyant sur **Ctrl**+**Alt**+**X**.)

2. Cliquez sur l’icône **Épingler** pour ancrer la fenêtre **Boîte à outils**.

     ![Cliquer sur l’icône Épingler pour épingler la fenêtre Boîte à outils à l’IDE](../ide/media/vb-pin-the-toolbox-window.png)

3. Cliquez sur le contrôle **Button**, puis faites-le glisser sur le formulaire.

     ![Ajouter un bouton au formulaire](../ide/media/vb-add-a-button-to-form1.png)

4. Dans la section **Apparence** (ou la section **Polices**) de la fenêtre **Propriétés**, tapez `Click this`, puis appuyez sur **Entrée**.

     ![Ajouter du texte au bouton du formulaire](../ide/media/vb-button-control-text.png)

     (Si vous ne voyez pas la fenêtre **Propriétés**, ouvrez-la à partir de la barre de menus. Pour cela, cliquez sur **Affichage** > **Fenêtre Propriétés**. Vous pouvez aussi appuyer sur **F4**.)

5. Dans la section **Design** de la fenêtre **Propriétés**, remplacez le nom **Button1** par `btnClickThis`, puis appuyez sur **Entrée**.

     ![Ajouter une fonction au bouton du formulaire](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>Ajouter une étiquette au formulaire

Maintenant que nous avons ajouté un contrôle bouton pour créer une action, nous allons ajouter un contrôle étiquette auquel envoyer le texte.

1. Sélectionnez le contrôle **Label** dans la fenêtre **Boîte à outils**, puis faites-le glisser sur le formulaire en dessous du bouton **Click this**.

2. Dans la section **Design** de la fenêtre **Propriétés**, remplacez le nom **Label1** par `lblHelloWorld`, puis appuyez sur **Entrée**.

### <a name="add-code-to-the-form"></a>Ajouter du code au formulaire

1. Dans la fenêtre **Form1.vb &#91;Design&#93;** , double-cliquez sur le bouton **Click this** pour ouvrir la fenêtre **Form1.vb**.

      (Vous pouvez également développer **Form1.vb** dans **Explorateur de solutions**, puis cliquer sur **Form1**.)

2. Dans la fenêtre **Form1.vb**, entre la ligne **Private Sub** et la ligne **End Sub** (ou entre la ligne **Public Class Form1** et la ligne **End Class**), tapez le code suivant.

     ![Ajouter du code au formulaire](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Exécuter l'application

1. Cliquez sur le bouton **Démarrer** pour exécuter l’application.

     ![Cliquer sur Démarrer pour déboguer et exécuter l’application](../ide/media/vb-click-start-hello-world.png)

   Il se passe alors plusieurs choses. Dans l’IDE de Visual Studio, la fenêtre **Outils de diagnostic** et une fenêtre **Sortie** s’ouvrent. En dehors de l’IDE, une boîte de dialogue **Form1** s’affiche. Elle contient le bouton **Click this** et le texte **Label1**.

2. Cliquez sur le bouton **Click this** dans la boîte de dialogue **Form1**. Notez que le texte **Label1** devient **Hello World !** .

    ![Boîte de dialogue Form1 contenant le texte Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous en avez appris un peu plus sur Visual Basic et l’IDE de Visual Studio. Si vous souhaitez approfondir ce sujet, poursuivez avec un didacticiel que vous trouverez dans la section **Didacticiels** de la table des matières.

## <a name="see-also"></a>Voir aussi

* [Démarrage rapide : Créer une application console dans Visual Studio avec Visual Basic](quickstart-visual-basic-console.md)
* [En savoir plus sur Visual Basic IntelliSense](visual-basic-specific-intellisense.md)
