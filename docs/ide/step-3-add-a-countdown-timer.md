---
title: 'Étape 3 : ajouter un temporisateur'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b48669d04c40f2fe91aea80ad61779164b586c9c
ms.sourcegitcommit: 04a717340b4ab4efc82945fbb25dfe58add2ee4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
---
# <a name="step-3-add-a-countdown-timer"></a>Étape 3 : ajouter un temporisateur
Dans la troisième partie de ce didacticiel, vous allez ajouter un temporisateur pour suivre le nombre de secondes restantes avant la fin du temps imparti à la personne interrogée.  

> [!NOTE]
>  Cette rubrique fait partie d'une série de didacticiels sur les concepts de codage de base. Pour obtenir une vue d’ensemble du tutoriel, consultez [Tutoriel 2 : créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
## <a name="to-add-a-countdown-timer"></a>Pour ajouter un temporisateur  

1.  Ajoutez une variable de type entier appelée **timeLeft**, comme vous l’avez fait dans la procédure précédente. Votre code doit ressembler à ce qui suit.  

     [!code-vb[VbExpressTutorial3Step3#5](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_1.vb)]
     [!code-csharp[VbExpressTutorial3Step3#5](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_1.cs)]  

     À présent, vous avez besoin d'une méthode qui compte réellement les secondes, telles qu'une minuterie, et qui déclenche un événement après la durée que vous spécifiez.  
  
2.  Dans la fenêtre de conception, déplacez un contrôle <xref:System.Windows.Forms.Timer> de la catégorie **Composants** de la **boîte à outils** vers votre formulaire.  
  
     Le contrôle apparaît dans la zone grise en bas de la fenêtre de conception.  

3.  Dans le formulaire, sélectionnez l’icône **timer1** que vous venez d’ajouter et affectez à sa propriété **Interval** la valeur **1000**.  
  
     La valeur d'intervalle étant exprimée en millisecondes, une valeur de 1000 entraîne le déclenchement de l'événement <xref:System.Windows.Forms.Timer.Tick> à chaque seconde.  
  
4.  Dans le formulaire, double-cliquez sur le contrôle **Timer** ou choisissez-le, puis appuyez sur la touche **Entrée**.  
  
     L'éditeur de code apparaît et affiche la méthode du gestionnaire d'événements Tick que vous venez d'ajouter.  
  
5.  Ajoutez les instructions suivantes à la nouvelle méthode de gestionnaire d'événements.  

     [!code-vb[VbExpressTutorial3Step3#6](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_2.vb)]
     [!code-csharp[VbExpressTutorial3Step3#6](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_2.cs)]  
  
     Suite à ce que vous avez ajouté, la minuterie vérifie à chaque seconde si le temps est écoulé en déterminant si la variable de type entier **timeLeft** est supérieure à 0. Si tel est le cas, cela signifie qu'il reste du temps. Tout d'abord, la minuterie soustrait 1 à timeLeft, puis met à jour la propriété **Text** du contrôle **timeLabel** pour indiquer à la personne qui répond au questionnaire le nombre de secondes restantes.  
  
     Si le temps est écoulé, la minuterie s'arrête et modifie le texte du contrôle **timeLabel** pour qu'il affiche **Time's up!** (Temps écoulé) Un message annonce que le questionnaire est terminé et la réponse apparaît (ici, en ajoutant addend1 et addend2). La propriété **Enabled** du contrôle **startButton** a la valeur **true** afin que la personne interrogée puisse commencer un autre questionnaire.  
  
     Vous venez d'ajouter une instruction `if else` qui permet à vos programmes de prendre des décisions. Une instruction `if else` se présente comme suit.  

    > [!NOTE]
    >  L’exemple suivant est uniquement fourni à titre d’illustration, ne l’ajoutez pas à votre projet.  

    ```vb  
    If (something that your program will check) Then  
        ' One or more statements that will run  
        ' if what the program checked is true.   
    Else  
        ' One or more statements that will run  
        ' if what the program checked is false.  
    End If  
    ```  

    ```csharp  
    if (something that your program will check)  
    {  
        // One or more statements that will run  
        // if what the program checked is true.   
    }  
    else  
    {  
        // One or more statements that will run  
        // if what the program checked is false.  
    }  
    ```  

     Examinez attentivement l'instruction que vous avez ajoutée dans le bloc `else` pour afficher la réponse au problème d'addition.  

     [!code-vb[VbExpressTutorial3Step3#24](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_3.vb)]
     [!code-csharp[VbExpressTutorial3Step3#24](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_3.cs)]  
  
     L'instruction `addend1 + addend2` additionne les valeurs des deux variables. La première partie (`sum.Value`) utilise la propriété **Value** du contrôle NumericUpDown de somme pour afficher la réponse correcte. Vous utiliserez la même propriété ultérieurement pour vérifier les réponses du questionnaire.  
  
     Les personnes interrogées peuvent entrer plus facilement des nombres à l’aide d’un contrôle <xref:System.Windows.Forms.NumericUpDown>. C’est la raison pour laquelle vous en utilisez un pour les réponses aux problèmes mathématiques. Toutes les réponses possibles sont des nombres entiers compris entre 0 et 100. En conservant les valeurs par défaut des propriétés **Minimum**, **Maximum** et **DecimalPlaces**, vous vous assurez que les personnes interrogées ne peuvent pas entrer de nombres décimaux, de nombres négatifs ou de nombres trop élevés. (Si vous vouliez permettre aux personnes répondant au questionnaire d’entrer 3,141 mais pas 3,1415, vous auriez dû affecter la valeur 3 à la propriété **DecimalPlaces**.)  

6.  Ajoutez trois lignes à la fin de la méthode `StartTheQuiz()`, pour que votre code ressemble à celui ci-dessous.  

     [!code-vb[VbExpressTutorial3Step3#7](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_4.vb)]
     [!code-csharp[VbExpressTutorial3Step3#7](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_4.cs)]  
  
     À présent, lorsque votre questionnaire démarre, il affecte la valeur 30 à la variable **timeLeft** et la propriété **Text** du contrôle **timeLabel** est définie à 30 secondes. Il appelle ensuite la méthode <xref:System.Windows.Forms.Timer.Start> du contrôle Timer pour démarrer le compte à rebours. (Le questionnaire ne vérifie pas encore la réponse : cette action est effectuée plus tard.)  
  
7.  Enregistrez votre programme, exécutez-le, puis choisissez le bouton **Démarrer** sur le formulaire.  

     La minuterie commence le compte à rebours. Lorsque le temps est écoulé, le questionnaire se termine et la réponse s'affiche. L'illustration suivante montre le questionnaire en cours.  

     ![Questionnaire mathématique en cours](../ide/media/express_addcountdown.png "Express_AddCountdown")  
Questionnaire mathématique en cours  

## <a name="to-continue-or-review"></a>Pour continuer ou examiner  
  
-   Pour passer à l’étape suivante du tutoriel, consultez [Étape 4 : ajouter la méthode CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).  
  
-   Pour revenir à l’étape précédente du tutoriel, consultez [Étape 2 : créer un problème d’addition aléatoire](../ide/step-2-create-a-random-addition-problem.md).
