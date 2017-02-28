---
title: "Étape 4 : ajouter la méthode CheckTheAnswer() | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
caps.latest.revision: 19
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 3eca055f2b4c5767d6713aea2eb73f7d70d9dd85
ms.lasthandoff: 02/22/2017

---
# <a name="step-4-add-the-checktheanswer-method"></a>Étape 4 : ajouter la méthode CheckTheAnswer()
Dans la quatrième partie de ce didacticiel, vous allez écrire une méthode, `CheckTheAnswer()`, permettant de déterminer si les réponses aux problèmes mathématiques sont correctes. Cette rubrique fait partie d'une série de didacticiels sur les concepts de codage de base. Pour obtenir une vue d’ensemble du didacticiel, consultez [Didacticiel 2 : créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
> [!NOTE]
>  Si vous programmez en Visual Basic, vous utiliserez le mot clé `Function` à la place du mot clé `Sub` habituel, car cette méthode retourne une valeur. En effet, contrairement aux procédures Function, les procédures Sub ne retournent aucune valeur.  
  
### <a name="to-verify-whether-the-answers-are-correct"></a>Pour vérifier si les réponses sont correctes  
  
1.  Ajoutez la méthode `CheckTheAnswer()`.  
  
     Quand cette méthode est appelée, elle ajoute les valeurs d’addend1 et d’addend2, puis compare le résultat à la valeur dans le contrôle `NumericUpDown` de somme. Si les valeurs sont égales, la méthode retourne la valeur `true`. Dans le cas contraire, la méthode retourne la valeur `false`. Votre code doit ressembler à ce qui suit.  
  
     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-cs[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]  
  
     Vous vérifierez ensuite la réponse en mettant à jour le code dans la méthode afin que le gestionnaire d'événements Tick du minuteur appelle la nouvelle méthode `CheckTheAnswer()`.  
  
2.  Ajoutez le code suivant dans l'instruction `if else`.  
  
     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-cs[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]  
  
     Si la réponse est correcte, `CheckTheAnswer()` retourne `true`. Le gestionnaire d’événements arrête le minuteur, affiche un message de félicitations, puis rend le bouton **Démarrer** à nouveau disponible. Dans le cas contraire, le questionnaire continue.  
  
3.  Enregistrez le programme, exécutez-le, démarrez un questionnaire et fournissez une réponse correcte au problème d'addition.  
  
    > [!NOTE]
    >  Lorsque vous écrivez la réponse, sélectionnez la valeur par défaut avant de commencer à écrire votre réponse, ou supprimez le zéro manuellement. Vous corrigerez ce comportement ultérieurement dans ce didacticiel.  
  
     Quand vous fournissez une réponse correcte, une boîte de message s’ouvre, le bouton **Démarrer** devient disponible et le minuteur s’arrête.  
  
### <a name="to-continue-or-review"></a>Pour continuer ou examiner  
  
-   Pour passer à l’étape suivante du didacticiel, consultez [Étape 5 : ajouter des gestionnaires d’événements d’entrée pour les contrôles NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).  
  
-   Pour revenir à l’étape précédente du didacticiel, consultez [Étape 3 : ajouter un temporisateur.](../ide/step-3-add-a-countdown-timer.md).
