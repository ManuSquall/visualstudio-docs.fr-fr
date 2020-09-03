---
title: 'Étape 3 : Assigner une icône aléatoire à chaque contrôle Label | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4382a450051b7626a5eb5e29bf2ce4e78f6eceda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671827"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Étape 3 : Assigner une icône aléatoire à chaque contrôle Label
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si les icônes se trouvent dans les mêmes cellules à chaque partie, le jeu ne sera pas intéressant. Pour éviter cela, affectez les icônes de façon aléatoire aux contrôles Label du formulaire en utilisant une méthode `AssignIconsToSquares()`.

### <a name="to-assign-a-random-icon-to-each-label"></a>Pour assigner une icône aléatoire à chaque contrôle Label

1. Avant d'ajouter le code suivant, examinez le fonctionnement de la méthode. Il y a un nouveau mot clé : `foreach` en Visual C# et `For Each` en Visual Basic. (L'une des lignes est commentée exprès, comme expliqué à la fin de cette procédure.)

     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#2)]

2. Ajoutez la méthode `AssignIconsToSquares()`, comme indiqué dans l'étape précédente. Vous pouvez le placer juste sous le code que vous avez ajouté à l' [étape 2 : ajouter un objet aléatoire et une liste d’icônes](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).

     Comme mentionné précédemment, il y a un élément nouveau dans votre méthode `AssignIconsToSquares()` : une boucle `foreach` en Visual C# et `For Each` en Visual Basic. Vous pouvez utiliser une boucle `For Each` chaque fois que vous voulez répéter plusieurs fois une action. Ici, vous souhaitez exécuter les mêmes instructions pour chaque contrôle Label dans votre TableLayoutPanel, comme l'illustre le code suivant. La première ligne crée une variable nommée `control` qui stocke chaque contrôle un par un, lorsque les instructions de la boucle de ce contrôle sont exécutées.

     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#14)]

    > [!NOTE]
    > Les noms « iconLabel » et « control » sont utilisés car ils sont explicites. Vous pouvez les remplacer par des noms quelconques : le code fonctionnera exactement de la même façon à condition que vous modifiiez le nom dans chaque instruction à l'intérieur de la boucle.

     La méthode `AssignIconsToSquares()` effectue une itération sur les contrôles Label dans le TableLayoutPanel et exécute les mêmes instructions pour chacun d'eux. Ces instructions extraient une icône aléatoire de la liste que vous avez ajoutée à l' [étape 2 : ajouter un objet aléatoire et une liste d’icônes](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (C'est la raison pour laquelle vous avez inclus deux fois chaque icône dans la liste : ainsi, des paires d'icônes sont assignées de façon aléatoire aux contrôles Label.)

     Examinez plus attentivement le code qui s'exécute à l'intérieur de la boucle `foreach` ou `For Each`. Ce code est reproduit ici.

     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#16)]

     La première ligne convertit la variable `control` en un contrôle Label nommé `iconLabel`. La ligne suivante est une instruction `if` qui vérifie si la conversion a été effectuée. Si tel n'est pas le cas, les instructions figurant dans l'instruction `if` sont exécutées. (Comme vous pouvez le rappeler dans les didacticiels précédents, l' `if` instruction est utilisée pour évaluer la condition que vous spécifiez.) La première ligne de l' `if` instruction crée une variable nommée `randomNumber` qui contient un nombre aléatoire qui correspond à l’un des éléments de la liste d’icônes. Pour cela, elle utilise la méthode `Next` de l'objet `Random` que vous avez créé précédemment. La méthode `Next` retourne le nombre aléatoire. Cette ligne utilise également la propriété `Count` de la liste `icons` pour déterminer la plage dans laquelle choisir le nombre aléatoire. La ligne suivante affecte un des éléments de la liste d'icônes à la propriété `Text` de l'étiquette. La ligne de commentaire est expliquée plus loin dans cette rubrique. Enfin, la dernière ligne de l'instruction `if` supprime de la liste l'icône ajoutée au formulaire.

     Rappelez-vous que si vous n'êtes pas sûr de ce que fait une partie du code, vous pouvez placez le pointeur de la souris sur un élément du code et lire l'info-bulle qui s'affiche. Vous pouvez également parcourir pas à pas chaque ligne de code pendant l'exécution du programme en utilisant le débogueur Visual Studio. Pour plus d’informations, consultez [Guide pratique pour exécuter pas à pas avec le débogueur Visual Studio](https://msdn.microsoft.com/vstudio/ee672313.aspx) ou [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md).

3. Pour remplir la grille de jeu d'icônes, vous devez appeler la méthode `AssignIconsToSquares()` dès que le programme démarre. Si vous utilisez Visual C#, ajoutez une instruction juste sous l’appel à la méthode `InitializeComponent()` dans le `Form1`*constructeur*, de sorte que votre formulaire appelle votre nouvelle méthode pour se configurer lui-même avant d’être affiché. Les constructeurs sont appelées lorsque vous créez un objet, tel qu'une classe ou un struct. Pour plus d’informations, consultez [Constructeurs (guide de programmation C#)](https://msdn.microsoft.com/library/ace5hbzh.aspx) ou [Utilisation des constructeurs et des destructeurs](https://msdn.microsoft.com/library/2z08e49e%28v=vs.90%29.aspx) (Visual Basic).

     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#13)]

     Pour Visual Basic, ajoutez l'appel de méthode `AssignIconsToSquares()` à la méthode `Form1_Load` afin que le code ressemble au code ci-dessous.

    ```vb
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AssignIconsToSquares()
    End Sub
    ```

4. Enregistrez votre programme et exécutez-le. Il doit afficher un formulaire avec des icônes aléatoires assignées à chaque contrôle Label.

5. Fermez votre programme et exécutez-le à nouveau. Remarquez que des icônes différentes sont assignées à chaque contrôle Label, comme indiqué dans la figure ci-dessous.

     ![Jeu de combinaisons avec des icônes aléatoires](../ide/media/express-tut4step3.png "Express_Tut4Step3") Jeu de combinaisons avec des icônes aléatoires

     Les icônes sont désormais visibles car vous ne les avez pas masquées. Pour les dissimuler au joueur, vous pouvez définir la propriété `Forecolor` de chaque contrôle Label sur la même couleur que sa propriété `BackColor`.

    > [!TIP]
    > Une autre manière de masquer des contrôles, tels que les contrôles Label, consiste à définir leur propriété **Visible** sur `False`.

6. Pour masquer les icônes, arrêtez le programme et supprimez les marques de commentaire de la ligne commentée de code à l'intérieur de la boucle `For Each`.

     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#15)]

7. Dans la barre de menus, cliquez sur le bouton **Enregistrer tout** pour enregistrer votre programme, puis exécutez-le. Les icônes semblent avoir disparu (seul un arrière-plan bleu est affiché). En réalité, les icônes sont assignées aléatoirement et sont toujours présentes. Comme les icônes sont de la même couleur que l'arrière-plan, le joueur ne peut pas les voir. Après tout, le jeu ne serait pas très intéressant si le joueur pouvait voir toutes les icônes dès le début !

### <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du didacticiel, consultez [étape 4 : ajouter un gestionnaire d’événements Click à chaque étiquette](../ide/step-4-add-a-click-event-handler-to-each-label.md).

- Pour revenir à l’étape précédente du didacticiel, consultez [étape 2 : ajouter un objet aléatoire et une liste d’icônes](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).
