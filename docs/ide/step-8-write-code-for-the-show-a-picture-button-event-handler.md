---
title: Écrire du code pour le gestionnaire d’événements du bouton Afficher une image
description: Écrivez du code pour le gestionnaire d’événements du bouton afficher une image dans le didacticiel créer une visionneuse d’images.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5718bd976952557d9ff5f92a0522a672757a54e8
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038658"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Étape 8 : écrire du code pour le gestionnaire d'événements du bouton Afficher une image

Dans cette étape, vous allez faire fonctionner le bouton **afficher une image** comme suit :

- Quand un utilisateur clique sur ce bouton, l’application ouvre une <xref:System.Windows.Forms.OpenFileDialog> zone.

- Si un utilisateur ouvre un fichier image, l’application affiche cette image dans le <xref:System.Windows.Forms.PictureBox> .

L'IDE dispose d'un outil puissant appelé IntelliSense pour vous aider à écrire du code. À mesure que vous tapez du code, l’IDE ouvre une zone avec des saisies semi-automatiques suggérées pour les mots partiels que vous entrez.

IntelliSense tente de déterminer ce que vous souhaitez faire ensuite et passe automatiquement au dernier élément que vous choisissez dans la liste. Vous pouvez utiliser les touches de direction Haut et Bas pour parcourir la liste, ou continuer à taper des lettres pour limiter le nombre de choix. Quand vous voyez le choix qui vous intéresse, appuyez sur la touche **Tab** pour le sélectionner. Sinon, vous pouvez ignorer les suggestions, si vous n'en avez pas besoin.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Pour écrire du code pour le gestionnaire d'événements du bouton Afficher une image

1. Ouvrez le **Concepteur Windows Forms** et double-cliquez sur le bouton **Afficher une image**. L’IDE accède immédiatement au concepteur de code et déplace votre curseur afin qu’il se trouve à l’intérieur de la `showButton_Click()` méthode (ou `ShowButton_Click()` ) que vous avez ajoutée précédemment.

1. Tapez un `i` sur la ligne vide entre les deux accolades `{ }`. (Dans Visual Basic, tapez sur la ligne vide comprise entre `Private Sub...` et `End Sub` .) Une fenêtre **IntelliSense** s’ouvre, comme illustré dans l’image suivante.

    ![IntelliSense avec code Visual C&#35;](../ide/media/express_ifintellisense.png)

    > [!NOTE]
    > Votre code risque de ne pas afficher de gestionnaires d’événements dans les lettres « la casse mixte ».

1. La fenêtre **IntelliSense** doit mettre en surbrillance le mot `if` . (Dans le cas contraire, entrez une minuscule `f` , et c’est le cas.) Notez qu’une *info-bulle* située en regard de la fenêtre **IntelliSense** apparaît avec la description, **extrait de code pour l’instruction if**. (Dans Visual Basic, l’info-bulle indique également qu’il s’agit d’un extrait de code, mais avec un libellé légèrement différent.) Vous souhaitez utiliser cet extrait de code, appuyez donc sur la touche **Tab** pour l’insérer `if` dans votre code. Appuyez ensuite à nouveau sur la touche **Tab** pour utiliser l’extrait de code `if`. (Si vous avez effectué un autre choix et si votre fenêtre **IntelliSense** a disparu, revenez en arrière pour effacer le `i` et retapez-le pour que la fenêtre **IntelliSense** s’ouvre à nouveau.)

    ![Code Visual C&#35;](../ide/media/express_highlighttrue.png)

### <a name="use-intellisense-to-enter-more-code"></a>Utiliser IntelliSense pour entrer davantage de code

Ensuite, utilisez IntelliSense pour entrer le reste du code destiné à ouvrir une boîte de dialogue **Ouvrir un fichier**. Si l’utilisateur a choisi le bouton **OK**, le contrôle PictureBox charge le fichier que l’utilisateur a sélectionné. Les étapes suivantes montrent comment entrer le code, et bien qu’il y ait de nombreuses étapes, il s’agit simplement de quelques séquences de touches :

 1. Commencez avec le texte sélectionné **true** dans l’extrait de code. Tapez `op` pour le remplacer. (En Visual Basic, comme vous devez commencer par une majuscule, tapez `Op`.)

 1. La fenêtre **IntelliSense** s’ouvre et affiche **openFileDialog1**. Appuyez sur la touche **Tab** pour sélectionner ce composant. (En Visual Basic, comme chaque mot commence par une majuscule, il est écrit **OpenFileDialog1**. Vérifiez que **OpenFileDialog1** est sélectionné.)

     Pour en savoir plus sur `OpenFileDialog`, consultez [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

 1. Tapez un point ( `.` ) (de nombreux programmeurs appellent ce point.) Étant donné que vous avez tapé un point juste après **OpenFileDialog1**, une fenêtre **IntelliSense** s’ouvre et contient toutes les propriétés et les méthodes du composant **OpenFileDialog** . Ce sont les mêmes propriétés qui s’affichent dans la fenêtre **Propriétés** quand vous effectuez ce choix dans le **Concepteur Windows Forms**. Vous pouvez également choisir des méthodes qui peuvent indiquer au composant d'effectuer certaines opérations (comme ouvrir une boîte de dialogue).

    > [!NOTE]
    > La fenêtre **IntelliSense** vous donne accès à des propriétés et à des méthodes. Pour déterminer ce qui est affiché, regardez l’icône à gauche de chaque élément dans la fenêtre **IntelliSense**. Vous voyez une image d’un bloc en regard de chaque méthode et une image d’une clé (ou d’un côté de clé) en regard de chaque propriété. Il y a également une icône d'éclair en regard de chaque événement. <br><br>Voici les icônes qui s’affichent :<br><br>![Icône Méthode](../ide/media/express_iconmethod.png)<br>![Icône Propriété](../ide/media/express_iconproperty.png)<br>![Icône Événement](../ide/media/express_iconevent.png)

 1. Commencez à taper `ShowDialog` (les majuscules n’ont aucune importance dans IntelliSense). La méthode `ShowDialog()` affichera la boîte de dialogue **Ouvrir un fichier**. Une fois que la fenêtre a mis **ShowDialog** en surbrillance, appuyez sur la touche **Tab**. Vous pouvez également sélectionner « ShowDialog » et choisir la touche **F1** pour obtenir de l’aide.

    Pour en savoir plus sur la méthode `ShowDialog()`, consultez [ShowDialog, méthode](<xref:System.Windows.Forms.Form.ShowDialog%2A>).

 1. Quand vous utilisez une méthode sur un contrôle ou un composant (opération désignée sous le nom d’*appel de méthode*), vous devez ajouter des parenthèses. Ajoutez des parenthèses ouvrantes et fermantes immédiatement après le « g » dans `ShowDialog`: `()`. Le code doit maintenant indiquer « openFileDialog1.ShowDialog() ».

    > [!NOTE]
    > Les méthodes sont une partie importante d’une application, et ce didacticiel a montré plusieurs façons d’utiliser des méthodes. Vous pouvez appeler la méthode d’un composant pour lui demander d’effectuer une action, comme quand vous avez appelé la méthode `ShowDialog()` du composant **OpenFileDialog**. Vous pouvez créer vos propres méthodes pour que votre application effectue des opérations, comme celle que vous générez maintenant, appelée la `showButton_Click()` méthode, qui ouvre une boîte de dialogue et une image lorsqu’un utilisateur choisit un bouton.

 1. Pour C#, ajoutez un espace, puis deux signes égal ( `==` ). Pour Visual Basic, ajoutez un espace, puis un seul signe égal (`=`). (C# et Visual Basic utilisent des opérateurs d’égalité différents.)

 1. Ajoutez un autre espace. Une fois terminé, une autre fenêtre **IntelliSense** s’ouvre. Commencez à taper `DialogResult` et appuyez sur la touche **Tab** pour l’ajouter.

    > [!NOTE]
    > Lorsque vous écrivez du code pour appeler une méthode, elle retourne parfois une valeur. Ici, la méthode <xref:System.Windows.Forms.CommonDialog.ShowDialog> du composant **OpenFileDialog** retourne une valeur <xref:System.Windows.Forms.DialogResult>. DialogResult est une valeur spéciale qui vous indique ce qui s'est passé dans une boîte de dialogue. Un composant **OpenFileDialog** permet à l’utilisateur de choisir **OK** ou **Annuler** : sa méthode `ShowDialog()` retournera donc `DialogResult.OK` ou `DialogResult.Cancel`.

 1. Tapez un point pour ouvrir la fenêtre **IntelliSense** de la valeur DialogResult. Tapez la lettre `O` et appuyez sur la touche **Tab pour in**sérer **OK**.

    Pour en savoir plus sur DialogResult, consultez [DialogResult](<xref:System.Windows.Forms.DialogResult>).

    > [!NOTE]
    > La première ligne de code doit être terminée. Pour C#, elle doit ressembler à ce qui suit.
    >
    >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
    >
    >  Pour Visual Basic, la ligne doit être la suivante.
    >
    >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

 1. Maintenant, ajoutez une ligne de code supplémentaire. Vous pouvez la taper (ou la copier et la coller), mais utilisez plutôt IntelliSense pour l'ajouter. Plus vous vous familiariserez avec IntelliSense, plus vous pourrez écrire votre propre code rapidement. Votre dernière `showButton_Click()` méthode doit ressembler au code suivant.

    [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

    [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]

    [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="next-steps"></a>Étapes suivantes

* Pour passer à l’étape suivante du didacticiel, consultez **[étape 9 : examiner, commenter et tester votre code](../ide/step-9-review-comment-and-test-your-code.md)**.

* Pour revenir à l’étape précédente du tutoriel, consultez [Étape 7 : ajouter des composants de dialogue à votre formulaire](../ide/step-7-add-dialog-components-to-your-form.md).

## <a name="see-also"></a>Voir aussi

* [Didacticiel 2 : créer un questionnaire mathématique chronométré](tutorial-2-create-a-timed-math-quiz.md)
* [Didacticiel 3 : créer un jeu de combinaisons](tutorial-3-create-a-matching-game.md)
