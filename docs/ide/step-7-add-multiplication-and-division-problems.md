---
title: "Étape 7 : ajouter des problèmes de multiplication et de division | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 17
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
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 481d1ad8050a0b028a7cbf23f9385c9920feb1a2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/06/2017

---
# <a name="step-7-add-multiplication-and-division-problems"></a>Étape 7 : ajouter des problèmes de multiplication et de division
Dans la septième partie de ce didacticiel, vous allez ajouter des problèmes de multiplication et de division, mais vous commencerez par réfléchir à la manière d'effectuer cette modification. Pensez à la première étape, dans laquelle vous devez stocker des valeurs.  
  
### <a name="to-add-multiplication-and-division-problems"></a>Pour ajouter des problèmes de multiplication et de division  
  
1.  Ajoutez quatre variables de type entier supplémentaires au formulaire.  
  
     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]  [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]  
  
2.  Comme vous l'avez fait auparavant, modifiez la méthode `StartTheQuiz()` pour renseigner les problèmes de multiplication et de division avec des nombres aléatoires.  
  
     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]  [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]  
  
3.  Modifiez la méthode `CheckTheAnswer()` afin qu'elle vérifie également les problèmes de multiplication et de division.  
  
     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]  [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]  
  
     Vous ne pouvez pas entrer aisément les signes de multiplication (×) et de division (÷) à l'aide du clavier, si bien que Visual C# et Visual Basic acceptent un astérisque (*) pour la multiplication et une barre oblique (/) pour la division.  
  
4.  Modifiez la dernière partie du gestionnaire d'événements Tick du minuteur afin que la réponse correcte s'affiche une fois le délai écoulé.  
  
     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]  [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]  
  
5.  Enregistrez et exécutez votre programme.  
  
     Les personnes interrogées doivent résoudre quatre problèmes pour terminer le questionnaire, comme le montre l'illustration ci-dessous.  
  
     ![Questionnaire mathématique avec quatre problèmes](../ide/media/express_finishedquiz.png "Express_FinishedQuiz")  
Questionnaire mathématique avec quatre problèmes  
  
### <a name="to-continue-or-review"></a>Pour continuer ou examiner  
  
-   Pour passer à l’étape suivante du didacticiel, consultez [Étape 8 : Personnaliser le questionnaire](../ide/step-8-customize-the-quiz.md).  
  
-   Pour revenir à l’étape précédente du didacticiel, consultez [Étape 6 : ajouter un problème de soustraction](../ide/step-6-add-a-subtraction-problem.md).
