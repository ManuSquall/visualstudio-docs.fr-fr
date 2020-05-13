---
title: 'Étape 7 : ajouter des composants de dialogue à votre formulaire'
ms.date: 08/30/2019
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9697bf6cf84c2a74daac2017b4f63d52a7019b6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579279"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Étape 7 : ajouter des composants de dialogue à votre formulaire

Pour permettre à votre application d’ouvrir des fichiers d’images <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.ColorDialog> de choisir une couleur d’arrière-plan, dans cette étape, vous ajoutez un composant et un composant à votre formulaire.

À certains égards, un composant est semblable à un contrôle. Utilisez la **boîte à outils** pour ajouter un composant à votre formulaire, et la fenêtre **Propriétés** pour définir les propriétés du composant. Mais contrairement à un contrôle, lorsque vous ajoutez un composant, il n'est pas visible dans votre formulaire. À la place, il permet d'utiliser des comportements que vous pouvez déclencher à l'aide de code. Un composant sert, par exemple, à ouvrir une boîte de dialogue **Ouvrir un fichier**.

## <a name="to-add-dialog-components-to-your-form"></a>Pour ajouter des composants de boîte de dialogue à votre formulaire

1. Choisissez le **concepteur de formulaires Windows** ( Form1.cs **[Design]**), puis ouvrez le groupe **Dialogs** dans la **boîte à outils**.

    > [!NOTE]
    > Le groupe **Boîtes de dialogue** dans la **boîte à outils** est doté de composants qui ouvrent de nombreuses boîtes de dialogue utiles. Vous pouvez les utiliser pour ouvrir et enregistrer des fichiers, parcourir des dossiers, ainsi que pour choisir des polices et des couleurs. Dans ce projet, vous utilisez deux composants de dialogue : OpenFileDialog et ColorDialog.

1. Pour ajouter un composant appelé **openFileDialog1** à votre formulaire, double-cliquez sur **OpenFileDialog**. Pour ajouter un composant appelé **colorDialog1** à votre formulaire, double-cliquez sur **ColorDialog** dans la **boîte à outils**. (Vous utilisez celui-ci dans l’étape suivante tutoriel.) Vous devriez voir une zone au bas de **Windows Forms Designer** (sous la forme De **visualiseur d’image)** qui a une icône pour chacun des deux composants de dialogue que vous avez ajouté, comme indiqué dans l’image suivante.

     ![Composants de dialogue](../ide/media/express_dialogsadded.png)<br>***Composants de dialogue*** *components*

1. Choisissez l’icône **openFileDialog1** dans la zone située en bas du **Concepteur Windows Forms**. Définissez deux propriétés :

    - Définissez la propriété **Filter** à la valeur suivante (vous pouvez copier-coller cette valeur) :

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Définissez la propriété **Title** à la valeur suivante : **Sélectionner un fichier image**

         Les paramètres de la propriété **Filter** spécifient les types de fichiers à afficher dans la boîte de dialogue **Sélectionner un fichier image**.

    > [!TIP]
    > Pour voir un exemple de boîte de dialogue **Ouvrir un fichier** dans une application différente, ouvrez le **Bloc-notes** ou **Paint** et, dans la barre de menus, choisissez **Fichier** > ** Ouvrir**. Remarquez comment il y a une liste d’abandon à côté du nom de fichier qui vous permet de choisir le type de fichier. <br/><br/>Vous venez d’utiliser la propriété **Filter** dans le composant **OpenFileDialog** pour configurer cela dans votre application. Notez également que les propriétés **Title** et **Filter** sont affichées en gras dans la fenêtre **Propriétés**. L'IDE utilise ce style pour vous montrer toutes les propriétés dont les valeurs par défaut ont été modifiées.

## <a name="next-steps"></a>Étapes suivantes

* Pour passer à l’étape suivante tutoriel, voir **[Step 8: Écrire du code pour le spectacle un gestionnaire d’événement bouton d’image](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)**.

* Pour revenir à l’étape précédente du tutoriel, consultez [Étape 6 : affecter un nom à vos contrôles bouton](../ide/step-6-name-your-button-controls.md).

## <a name="see-also"></a>Voir aussi

* [Tutorial 2: Créer un quiz de mathématiques chronométré](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Créer un jeu correspondant](tutorial-3-create-a-matching-game.md)
