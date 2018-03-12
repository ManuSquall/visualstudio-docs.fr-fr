---
title: "Étape 3 : Assigner une icône aléatoire à chaque contrôle Label | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
caps.latest.revision: "31"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f0e594e3ef4d0b08dcd957250f7645d40f6533e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Étape 3 : Assigner une icône aléatoire à chaque contrôle Label
Si les icônes se trouvent dans les mêmes cellules à chaque partie, le jeu ne sera pas intéressant. Pour éviter cela, affectez les icônes de façon aléatoire aux contrôles Label du formulaire en utilisant une méthode `AssignIconsToSquares()`.  
  
### <a name="to-assign-a-random-icon-to-each-label"></a>Pour assigner une icône aléatoire à chaque contrôle Label  
  
1.  Avant d'ajouter le code suivant, examinez le fonctionnement de la méthode. Il y a un nouveau mot clé : `foreach` en Visual C# et `For Each` en Visual Basic. (L'une des lignes est commentée exprès, comme expliqué à la fin de cette procédure.)  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_1.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_1.vb)]  
  
2.  Ajoutez la méthode `AssignIconsToSquares()`, comme indiqué dans l'étape précédente. Vous pouvez l’insérer juste en dessous du code que vous avez ajouté à l’[Étape 2 : Ajouter un objet aléatoire et une liste d’icônes](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).  
  
     Comme mentionné précédemment, il y a un élément nouveau dans votre méthode `AssignIconsToSquares()` : une boucle `foreach` en Visual C# et `For Each` en Visual Basic. Vous pouvez utiliser une boucle `For Each` chaque fois que vous voulez répéter plusieurs fois une action. Ici, vous souhaitez exécuter les mêmes instructions pour chaque contrôle Label dans votre TableLayoutPanel, comme l'illustre le code suivant. La première ligne crée une variable nommée `control` qui stocke chaque contrôle un par un, lorsque les instructions de la boucle de ce contrôle sont exécutées.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_2.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_2.vb)]  
  
    > [!NOTE]
    >  Les noms « iconLabel » et « control » sont utilisés car ils sont explicites. Vous pouvez les remplacer par des noms quelconques : le code fonctionnera exactement de la même façon à condition que vous modifiiez le nom dans chaque instruction à l'intérieur de la boucle.  
  
     La méthode `AssignIconsToSquares()` effectue une itération sur les contrôles Label dans le TableLayoutPanel et exécute les mêmes instructions pour chacun d'eux. Ces instructions tirent une icône aléatoire de la liste que vous avez ajoutée à l’[Étape 2 : Ajouter un objet aléatoire et une liste d’icônes](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (C'est la raison pour laquelle vous avez inclus deux fois chaque icône dans la liste : ainsi, des paires d'icônes sont assignées de façon aléatoire aux contrôles Label.)  
  
     Examinez plus attentivement le code qui s'exécute à l'intérieur de la boucle `foreach` ou `For Each`. Ce code est reproduit ici.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_3.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_3.vb)]  
  
     La première ligne convertit la variable `control` en un contrôle Label nommé `iconLabel`. La ligne suivante est une instruction `if` qui vérifie si la conversion a été effectuée. Si tel n'est pas le cas, les instructions figurant dans l'instruction `if` sont exécutées. (Comme nous l'avons vu dans les didacticiels précédents, l'instruction `if` permet d'évaluer toute condition que vous spécifiez.) La première ligne de l'instruction `if` crée une variable nommée `randomNumber`, qui contient un nombre aléatoire correspondant à l'un des éléments de la liste d'icônes. Pour cela, elle utilise la méthode `Next` de l'objet `Random` que vous avez créé précédemment. La méthode `Next` retourne le nombre aléatoire. Cette ligne utilise également la propriété `Count` de la liste `icons` pour déterminer la plage dans laquelle choisir le nombre aléatoire. La ligne suivante affecte un des éléments de la liste d'icônes à la propriété `Text` de l'étiquette. La ligne de commentaire est expliquée plus loin dans cette rubrique. Enfin, la dernière ligne de l'instruction `if` supprime de la liste l'icône ajoutée au formulaire.  
  
     Rappelez-vous que si vous n'êtes pas sûr de ce que fait une partie du code, vous pouvez placez le pointeur de la souris sur un élément du code et lire l'info-bulle qui s'affiche. Vous pouvez également parcourir pas à pas chaque ligne de code pendant l'exécution du programme en utilisant le débogueur Visual Studio. Pour plus d’informations, consultez [Guide pratique pour exécuter pas à pas avec le débogueur Visual Studio](http://msdn.microsoft.com/vstudio/ee672313.aspx) ou [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md).  
  
3.  Pour remplir la grille de jeu d'icônes, vous devez appeler la méthode `AssignIconsToSquares()` dès que le programme démarre. Si vous utilisez Visual C#, ajoutez une instruction juste sous l’appel à la méthode `InitializeComponent()` dans le `Form1`*constructeur*, de sorte que votre formulaire appelle votre nouvelle méthode pour se configurer lui-même avant d’être affiché. Les constructeurs sont appelées lorsque vous créez un objet, tel qu'une classe ou un struct. Pour plus d’informations, consultez [Constructeurs (guide de programmation C#)](http://msdn.microsoft.com/library/ace5hbzh.aspx) ou [Utilisation des constructeurs et des destructeurs](http://msdn.microsoft.com/library/2z08e49e.aspx) (Visual Basic).  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_4.cs)]  
  
     Pour Visual Basic, ajoutez l'appel de méthode `AssignIconsToSquares()` à la méthode `Form1_Load` afin que le code ressemble au code ci-dessous.  
  
    ```vb  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AssignIconsToSquares()  
    End Sub  
    ```  
  
4.  Enregistrez votre programme et exécutez-le. Il doit afficher un formulaire avec des icônes aléatoires assignées à chaque contrôle Label.  
  
5.  Fermez votre programme et exécutez-le à nouveau. Remarquez que des icônes différentes sont assignées à chaque contrôle Label, comme indiqué dans la figure ci-dessous.  
  
     ![Jeu de combinaisons avec des icônes aléatoires](../ide/media/express_tut4step3.png "Express_Tut4Step3")  
Jeu de combinaisons avec des icônes aléatoires  
  
     Les icônes sont désormais visibles car vous ne les avez pas masquées. Pour les dissimuler au joueur, vous pouvez définir la propriété `Forecolor` de chaque contrôle Label sur la même couleur que sa propriété `BackColor`.  
  
    > [!TIP]
    >  Une autre manière de masquer des contrôles, tels que les contrôles Label, consiste à définir leur propriété **Visible** sur `False`.  
  
6.  Pour masquer les icônes, arrêtez le programme et supprimez les marques de commentaire de la ligne commentée de code à l'intérieur de la boucle `For Each`.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/CSharp/step-3-assign-a-random-icon-to-each-label_5.cs)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../ide/codesnippet/VisualBasic/step-3-assign-a-random-icon-to-each-label_5.vb)]  
  
7.  Dans la barre de menus, cliquez sur le bouton **Enregistrer tout** pour enregistrer votre programme, puis exécutez-le. Les icônes semblent avoir disparu (seul un arrière-plan bleu est affiché). En réalité, les icônes sont assignées aléatoirement et sont toujours présentes. Comme les icônes sont de la même couleur que l'arrière-plan, le joueur ne peut pas les voir. Après tout, le jeu ne serait pas très intéressant si le joueur pouvait voir toutes les icônes dès le début !  
  
### <a name="to-continue-or-review"></a>Pour continuer ou examiner  
  
-   Pour passer à l’étape suivante du didacticiel, consultez [Étape 4 : Ajouter un gestionnaire d’événements Click à chaque contrôle Label](../ide/step-4-add-a-click-event-handler-to-each-label.md).  
  
-   Pour revenir à l’étape précédente du didacticiel, consultez [Étape 2 : Ajouter un objet aléatoire et une liste d’icônes](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).