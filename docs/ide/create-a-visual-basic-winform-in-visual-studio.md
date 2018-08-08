---
title: Créer une application Windows Forms dans Visual Studio avec Visual Basic
description: Découvrez comment créer une application Windows Forms dans Visual Studio avec Visual Basic, étape par étape.
ms.custom: ''
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 0468a3ee546659d8079d98f49b196819c44afbd1
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381658"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Créer une application Windows Forms dans Visual Studio avec Visual Basic

Dans cette courte présentation de l’environnement de développement intégré (IDE) de Visual Studio, vous allez créer une application Visual Basic simple qui comporte une interface utilisateur Windows.

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) pour l’installer gratuitement.

## <a name="create-a-project"></a>Créer un projet

Tout d’abord, vous allez créer un projet d’application Visual Basic. Le type de projet inclut tous les fichiers de modèle dont vous aurez besoin au départ.

1. Ouvrez Visual Studio 2017.

2. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet**.

3. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **Visual Basic**, puis choisissez **Bureau Windows**. Dans le volet central, choisissez **Windows Forms App (.NET Framework)**. Nommez ensuite le fichier `HelloWorld`.

     Si vous ne voyez pas le modèle de projet **Windows Forms App (.NET Framework)**, quittez la boîte de dialogue **Nouveau projet** puis, dans la barre de menus supérieure, choisissez **Outils** > **Obtenir les outils et fonctionnalités**. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement .NET Desktop**, puis choisissez **Modifier**.

     ![Charge de travail .NET Core dans Visual Studio Installer](../ide/media/install-dot-net-desktop-env.png)

## <a name="create-the-application"></a>Créer l’application

Une fois que vous avez sélectionné votre modèle de projet Visual Basic et nommé votre fichier, Visual Studio ouvre un formulaire. Un formulaire est une interface utilisateur Windows. Nous allons créer une application « Hello World » en ajoutant des contrôles au formulaire, puis exécuter cette application.

### <a name="add-a-button-to-the-form"></a>Ajouter un bouton au formulaire

1. Cliquez sur **Boîte à outils** pour ouvrir la fenêtre volante Boîte à outils.

     ![Cliquer sur la boîte à outils pour ouvrir la fenêtre Boîte à outils](../ide/media/vb-toolbox-toolwindow.png)

     (Si vous ne voyez pas la fenêtre volante **Boîte à outils**, ouvrez-la à partir de la barre de menus. Pour cela, cliquez sur **Affichage** > **Boîte à outils**. Vous pouvez aussi appuyer sur **Ctrl**+**Alt**+**X**.)

2. Cliquez sur l’icône **Épingler** pour ancrer la fenêtre **Boîte à outils**.

     ![Cliquer sur l’icône Épingler pour épingler la fenêtre Boîte à outils à l’IDE](../ide/media/vb-pin-the-toolbox-window.png)
3. Cliquez sur le contrôle **Button**, puis faites-le glisser sur le formulaire.

     ![Ajouter un bouton au formulaire](../ide/media/vb-add-a-button-to-form1.png)

4. Dans la section **Apparence** de la fenêtre **Propriétés**, tapez `Click this`, puis appuyez sur **Entrée**.

     ![Ajouter du texte au bouton du formulaire](../ide/media/vb-button-control-text.png)

     (Si vous ne voyez pas la fenêtre **Propriétés**, ouvrez-la à partir de la barre de menus. Pour cela, cliquez sur **Affichage** > **Fenêtre Propriétés**. Vous pouvez aussi appuyer sur **F4**.)

5. Dans la section **Design** de la fenêtre **Propriétés**, remplacez le nom **Button1** par `btnClickThis`, puis appuyez sur **Entrée**.

     ![Ajouter une fonction au bouton du formulaire](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>Ajouter une étiquette au formulaire

Maintenant que nous avons ajouté un contrôle bouton pour créer une action, nous allons ajouter un contrôle étiquette auquel envoyer le texte.

1. Sélectionnez le contrôle **Label** dans la fenêtre **Boîte à outils**, puis faites-le glisser sur le formulaire en dessous du bouton **Click this**.

2. Dans la section **Design** de la fenêtre **Propriétés**, remplacez le nom **Label1** par `lblHelloWorld`, puis appuyez sur **Entrée**.

### <a name="add-code-to-the-form"></a>Ajouter du code au formulaire

1. Dans la fenêtre **Form1.vb &#91;Design&#93;**, double-cliquez sur le bouton **Click this** pour ouvrir la fenêtre **Form1.vb**.

      (Vous pouvez également développer **Form1.vb** dans **Explorateur de solutions**, puis cliquer sur **Form1**.)

2. Dans la fenêtre **Form1.vb**, entre la ligne **Private Sub** et la ligne **End Sub**, tapez ou collez `lblHelloWorld.Text = "Hello World!"`.

     ![Ajouter du code au formulaire](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Exécuter l'application

1. Cliquez sur le bouton **Démarrer** pour exécuter l’application.

     ![Cliquer sur Démarrer pour déboguer et exécuter l’application](../ide/media/vb-click-start-hello-world.png)

   Il se passe alors plusieurs choses. Dans l’IDE de Visual Studio, la fenêtre **Outils de diagnostic** et une fenêtre **Sortie** s’ouvrent. En dehors de l’IDE, une boîte de dialogue **Form1** s’affiche. Elle contient le bouton **Click this** et le texte **Label1**.

2. Cliquez sur le bouton **Click this** dans la boîte de dialogue **Form1**. Notez que le texte **Label1** devient **Hello World !**.

    ![Boîte de dialogue Form1 contenant le texte Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

Félicitations ! Vous avez terminé ce guide de démarrage rapide. Nous espérons que vous en avez appris un peu plus sur Visual Basic et l’IDE de Visual Studio. Si vous souhaitez approfondir ce sujet, poursuivez avec un didacticiel que vous trouverez dans la section **Didacticiels** de la table des matières.

## <a name="see-also"></a>Voir aussi

* [Démarrage rapide : Créer une application console dans Visual Studio avec Visual Basic](quickstart-visual-basic-console.md)
* [En savoir plus sur Visual Basic IntelliSense](visual-basic-specific-intellisense.md)
