---
title: 'Étape 3 : assigner une icône aléatoire à chaque étiquette'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 366f6d7a07d2f30b5b8110fb7dae7a2311fcce23
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579398"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Étape 3 : assigner une icône aléatoire à chaque étiquette

Si les icônes se trouvent dans les mêmes cellules à chaque partie, le jeu ne sera pas intéressant. Pour éviter cela, affectez les icônes de façon aléatoire aux contrôles d’étiquettes de votre formulaire en utilisant une méthode `AssignIconsToSquares()`.

## <a name="to-assign-a-random-icon-to-each-label"></a>Pour assigner une icône aléatoire à chaque contrôle Label

1. Avant d'ajouter le code suivant, examinez le fonctionnement de la méthode. Il y a un `foreach` nouveau mot `For Each` clé : dans C et dans Visual Basic. (L'une des lignes est commentée exprès, comme expliqué à la fin de cette procédure.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]

      > [!IMPORTANT]
      > Utilisez le contrôle du langage de programmation en haut à droite de cette page pour voir l’extrait de code CMD ou l’extrait de code Visual Basic.<br><br>![Contrôle linguistique de programmation pour Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

2. Ajoutez la méthode `AssignIconsToSquares()`, comme indiqué dans l'étape précédente. Vous pouvez l’insérer juste en dessous du code que vous avez ajouté à l’[Étape 2 : ajouter un objet aléatoire et une liste d’icônes](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Comme mentionné précédemment, il ya `AssignIconsToSquares()` quelque chose `foreach` de nouveau `For Each` dans votre méthode: une boucle en C et dans Visual Basic. Vous pouvez utiliser une boucle `For Each` chaque fois que vous voulez répéter plusieurs fois une action. Ici, vous souhaitez exécuter les mêmes instructions pour chaque étiquette dans votre <xref:System.Windows.Forms.TableLayoutPanel>, comme l'illustre le code suivant. La première ligne crée une variable nommée `control` qui stocke chaque contrôle un par un, lorsque les instructions de la boucle de ce contrôle sont exécutées.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]

    > [!NOTE]
    > Les noms « iconLabel » et « control » sont utilisés car ils sont explicites. Vous pouvez les remplacer par des noms quelconques : le code fonctionnera exactement de la même façon à condition que vous modifiiez le nom dans chaque instruction à l'intérieur de la boucle.

     La méthode `AssignIconsToSquares()` effectue une itération sur les contrôles Label dans le TableLayoutPanel et exécute les mêmes instructions pour chacun d'eux. Ces instructions tirent une icône aléatoire de la liste que vous avez ajoutée à l’[Étape 2 : ajouter un objet aléatoire et une liste d’icônes](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (C'est la raison pour laquelle vous avez inclus deux fois chaque icône dans la liste : ainsi, des paires d'icônes sont assignées de façon aléatoire aux contrôles d’étiquettes.)

     Examinez plus attentivement le code qui s'exécute à l'intérieur de la boucle `foreach` ou `For Each`. Ce code est reproduit ici.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]

     La première ligne convertit la variable **contrôle** en étiquette nommée **iconLabel**. La ligne suivante est une instruction `if` qui vérifie si la conversion a été effectuée. Si tel n'est pas le cas, les instructions figurant dans l'instruction `if` sont exécutées. (Comme vous vous en souvenez peut-être des tutoriels précédents, la `if` déclaration est utilisée pour évaluer n’importe quelle condition que vous spécifiez.) La première ligne `if` de l’instruction crée une variable nommée **randomNumber** qui contient un nombre aléatoire qui correspond à l’un des éléments de la liste des icônes. Pour cela, elle utilise la méthode <xref:System.Random.Next> de l'objet <xref:System.Random> que vous avez créé précédemment. La méthode `Next` retourne le nombre aléatoire. Cette ligne utilise également la propriété <xref:System.Collections.Generic.List%601.Count> de la liste d’**icônes** pour déterminer la plage dans laquelle choisir le nombre aléatoire. La ligne suivante affecte un des éléments de la liste d'icônes à la propriété <xref:System.Windows.Forms.Label.Text> de l'étiquette. La ligne de commentaire est expliquée plus loin dans cette rubrique. Enfin, la dernière ligne de l'instruction `if` supprime de la liste l'icône ajoutée au formulaire.

     Rappelez-vous que si vous n'êtes pas sûr de ce que fait une partie du code, vous pouvez placez le pointeur de la souris sur un élément du code et lire l'info-bulle qui s'affiche. Vous pouvez également parcourir pas à pas chaque ligne de code pendant l'exécution du programme en utilisant le débogueur Visual Studio. Pour plus d’informations, consultez [Comment utiliser le débogueur dans Visual Studio ?](https://msdn.microsoft.com/vstudio/ee672313.aspx) ou [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md).

3. Pour remplir la grille de jeu d'icônes, vous devez appeler la méthode `AssignIconsToSquares()` dès que le programme démarre. Si vous utilisez C, ajoutez une déclaration juste `InitializeComponent()` en dessous de l’appel à la méthode dans le_constructeur_ **Form1,** de sorte que votre formulaire appelle votre nouvelle méthode pour se configurer avant qu’elle ne soit affichée. Les constructeurs sont appelées lorsque vous créez un objet, tel qu'une classe ou un struct. Pour plus d’informations, consultez [Constructeurs (guide de programmation C#)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) ou [Utilisation des constructeurs et des destructeurs](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)) (Visual Basic).

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]

     Pour Visual Basic, ajoutez l'appel de méthode `AssignIconsToSquares()` à la méthode `Form1_Load` afin que le code ressemble au code ci-dessous.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Enregistrez votre programme et exécutez-le. Il doit afficher un formulaire avec des icônes aléatoires assignées à chaque contrôle Label.

5. Fermez votre programme et exécutez-le à nouveau. Remarquez que des icônes différentes sont assignées à chaque contrôle Label, comme indiqué dans la figure ci-dessous.

     ![Jeu de combinaisons avec des icônes aléatoires](../ide/media/express_tut4step3.png)<br/>
*Jeu de combinaisons avec des icônes aléatoires*

     Les icônes sont désormais visibles car vous ne les avez pas masquées. Pour les dissimuler au joueur, vous pouvez définir la propriété **ForeColor** de chaque étiquette sur la même couleur que sa propriété **BackColor**.

    > [!TIP]
    > Une autre manière de masquer les contrôles tels que des étiquettes consiste à définir leur propriété **Visible** sur **False**.

6. Pour masquer les icônes, arrêtez le programme et supprimez les marques de commentaire de la ligne commentée de code à l'intérieur de la boucle `For Each`.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]

7. Dans la barre de menus, cliquez sur le bouton **Enregistrer tout** pour enregistrer votre programme, puis exécutez-le. Les icônes semblent avoir disparu (seul un arrière-plan bleu est affiché). En réalité, les icônes sont assignées aléatoirement et sont toujours présentes. Comme les icônes sont de la même couleur que l'arrière-plan, le joueur ne peut pas les voir. Après tout, le jeu ne serait pas très intéressant si le joueur pouvait voir toutes les icônes dès le début !

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante tutoriel, voir **[Étape 4: Ajouter un gestionnaire d’événements cliquez sur chaque étiquette](../ide/step-4-add-a-click-event-handler-to-each-label.md)**.

- Pour revenir à l’étape précédente du tutoriel, consultez [Étape 2 : ajouter un objet aléatoire et une liste d’icônes](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
