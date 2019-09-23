---
title: 'Étape 6 : Nommer vos contrôles bouton'
ms.date: 08/30/2016
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ce9f55dd54dbe85f64226c1ca7f0b4f75b1cdfc
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118697"
---
# <a name="step-6-name-your-button-controls"></a>Étape 6 : Nommer vos contrôles bouton

Votre formulaire ne contient qu’un seul <xref:System.Windows.Forms.PictureBox>. Lorsque vous l’avez ajouté, l’IDE l’a nommé automatiquement **pictureBox1**. Il n’existe qu’un seul <xref:System.Windows.Forms.CheckBox>, appelé **checkBox1**. Vous allez bientôt écrire du code et ce code fera référence à CheckBox et PictureBox. Étant donné qu’il n’existe qu’un seul de ces contrôles, vous saurez ce que cela signifie quand vous voyez **PictureBox1** ou **CheckBox1** dans votre code.

> [!TIP]
> En Visual Basic, le nom des contrôles commence par défaut par une lettre majuscule, autrement dit **PictureBox1**, **CheckBox1**et ainsi de suite.

Il existe quatre boutons dans votre formulaire, et l’IDE les a nommés **button1**, **button2**, **button3**et **button4**. Leurs noms actuels ne vous permettent pas de savoir s’il s’agit du bouton **Fermer** ou du bouton **Afficher une image** . C’est pourquoi il est utile de donner à vos contrôles bouton des noms plus informatifs.

## <a name="to-name-your-button-controls"></a>Pour nommer vos contrôles bouton

1. Dans le formulaire, choisissez le bouton **Fermer** . (Si tous les boutons sont encore sélectionnés, appuyez sur la touche **Échap** pour annuler la sélection.) Faites défiler jusqu’à la propriété **(Name)** dans la fenêtre **Propriétés**. (La propriété **(Name)** se trouve vers le haut quand les propriétés sont classées par ordre alphabétique.) Remplacez le nom par **BoutonFermer**, comme illustré dans la capture d’écran suivante.

    ![Fenêtre Propriétés avec nom closeButton](../ide/media/express_setnameproperty.png)<br>***Propriétés*** de *fenêtre avec* ***BoutonFermer*** *nom*

    > [!NOTE]
    > Essayez de modifier le nom de votre bouton pour **Fermer le bouton**, avec un espace entre les mots « Close » et « Button ». Dans ce cas, l’IDE affiche un message d’erreur : « Valeur de propriété non valide ». Les espaces (et quelques autres caractères) ne sont pas autorisés dans les noms de contrôle.

1. Renommez les trois autres boutons en **backgroundButton**, **clearButton**et **showButton**.
Vous pouvez vérifier les noms en sélectionnant la liste déroulante du sélecteur de contrôles dans la fenêtre **Propriétés** . Les nouveaux noms de boutons apparaissent.

1. Double-cliquez sur le bouton **Afficher une image** du formulaire. Vous pouvez également cliquer sur le bouton **afficher une image** sur le formulaire, puis appuyer sur la touche **entrée** . Dans ce cas, l’IDE ouvre un onglet supplémentaire dans la fenêtre principale nommée **Form1.cs**. (Si vous utilisez Visual Basic, l’onglet est nommé **Form1. vb**).

   Cet onglet affiche le fichier de code derrière le formulaire, comme illustré dans la capture d’écran suivante.

    ![Onglet Form1.cs avec code Visual C&#35;](../ide/media/express_showbuttoncode.png)<br>
Onglet ***Form1.cs*** *avec C# code*

    > [!NOTE]
    > Votre onglet Form1.cs ou Form1. vb peut afficher **showButton** comme **showButton** à la place.

1. Examinez attentivement cette partie du code.

    ```csharp
        private void ShowButton_Click(object sender, EventArgs e)
    {
    }
    ```

    ```vb
        Private Sub showButton_Click() Handles showButton.Click

    End Sub
    ```

   > [!IMPORTANT]
   > Utilisez le contrôle de langage de programmation en haut à droite de cette page pour afficher C# l’extrait de code ou le Visual Basic extrait de code.<br><br>![Contrôle du langage de programmation pour Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

   Vous examinez le code appelé `showButton_Click()` (ou `ShowButton_Click()`). L’IDE l’a ajouté au code du formulaire lorsque vous avez ouvert le fichier de code du bouton **showButton** . Au moment de la conception, lorsque vous ouvrez le fichier de code d’un contrôle dans un formulaire, le code est généré pour le contrôle s’il n’existe pas déjà. Ce code, connu sous le nom de *méthode*, s’exécute lorsque vous exécutez votre application et choisissez le contrôle (dans ce cas, le bouton **afficher une image** ).

1. Cliquez de nouveau sur l’onglet **Concepteur Windows Forms** (**Form1.cs [Design]** ), puis ouvrez le fichier de code du bouton **effacer l’image** pour créer une méthode pour celui-ci dans le code du formulaire. Répétez la même opération pour les deux boutons restants. Chaque fois, l’IDE ajoute une nouvelle méthode au fichier de code du formulaire.

1. Pour ajouter une méthode, ouvrez le fichier de code du contrôle **CheckBox** dans le **Concepteur Windows Forms** pour que l’IDE ajoute une méthode `checkBox1_CheckedChanged()`. Cette méthode est appelée chaque fois que l’utilisateur active ou désactive la case à cocher.

   > [!TIP]
   > Lorsque vous travaillez sur une application, vous passez souvent de l’éditeur de code à l' **Concepteur Windows Forms**. L’IDE vous permet de naviguer facilement dans votre projet. Utilisez **Explorateur de solutions** pour ouvrir **Concepteur Windows Forms** en double-cliquant sur Form1.cs C# dans ou sur *Form1. vb* dans Visual Basic, ou dans la barre de menus, choisissez**Concepteur**de **vues** > .

    Les éléments suivants montrent le nouveau code qui est affiché dans l’éditeur de code.

    [!code-csharp[VbExpressTutorial1Step6_#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

    [!code-vb[VbExpressTutorial1Step6_#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]

    > [!NOTE]
    > Votre code risque de ne pas afficher de gestionnaires d’événements dans les lettres « la casse mixte ».

    Les cinq méthodes que vous avez ajoutées sont appelées *gestionnaires d’événements*, car votre application les appelle chaque fois qu’un événement (par exemple, un utilisateur qui choisit un bouton ou une case à cocher) se produit.

    Lorsque vous affichez le code d’un contrôle dans l’IDE au moment de la conception, Visual Studio ajoute une méthode de gestionnaire d’événements pour le contrôle s’il n’en possède pas déjà une. Par exemple, lorsque vous double-cliquez sur un bouton, l’IDE ajoute un gestionnaire d’événements pour son événement <xref:System.Windows.Forms.Control.Click> (qui est appelé chaque fois que l’utilisateur choisit le bouton). Lorsque vous double-cliquez sur une case à cocher, l’IDE ajoute un gestionnaire d’événements pour son événement <xref:System.Windows.Forms.CheckBox.CheckedChanged> (qui est appelé chaque fois que l’utilisateur active ou désactive la case).

    Une fois que vous avez ajouté un gestionnaire d’événements pour un contrôle, vous pouvez y revenir à tout moment en double-cliquant sur le contrôle du **Concepteur Windows Forms** ou, dans la barre de menus, en choisissant **Afficher** > **Code**.

    Les noms sont importants lorsque vous générez des programmes, et vous pouvez nommer les méthodes (y compris les gestionnaires d’événements) comme vous le voulez. Lorsque vous ajoutez un gestionnaire d’événements avec l’IDE, il choisit un nom en fonction du nom du contrôle et de l’événement qui est géré.

    Par exemple, l’événement Click pour un bouton nommé **showButton** est appelé la `showButton_Click()` méthode de gestionnaire d' `ShowButton_Click()`événements (ou). De même, des parenthèses ouvrantes et fermantes `()` sont généralement ajoutées après le nom de la méthode pour indiquer clairement qu’il s’agit de méthodes.

    Si vous décidez de modifier un nom de variable de code, cliquez avec le bouton droit sur la variable dans le code, puis choisissez **Refactoriser** > **Renommer**. Toutes les instances de cette variable dans le code sont renommées. Pour plus d’informations, consultez [refactorisation de changement de nom](../ide/reference/rename.md).

## <a name="next-steps"></a>Étapes suivantes

* Pour passer à l’étape suivante du didacticiel, **consultez [étape 7 : Ajoutez des composants de boîte de](../ide/step-7-add-dialog-components-to-your-form.md)dialogue à votre formulaire**.

* Pour revenir à l’étape précédente du tutoriel, consultez [Étape 5 : Ajouter des contrôles à votre formulaire](../ide/step-5-add-controls-to-your-form.md).

## <a name="see-also"></a>Voir aussi

* [Tutoriel 2 : Créer un questionnaire mathématique chronométré](tutorial-2-create-a-timed-math-quiz.md)
* [Tutoriel 3 : Créer un jeu de combinaisons](tutorial-3-create-a-matching-game.md)
