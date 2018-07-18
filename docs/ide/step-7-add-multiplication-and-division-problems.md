---
title: 'Étape 7 : ajouter des problèmes de multiplication et de division'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0186ba637bdb1bc85a7ff60f23c9799972b6a931
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747904"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Étape 7 : ajouter des problèmes de multiplication et de division
Dans la septième partie de ce didacticiel, vous allez ajouter des problèmes de multiplication et de division, mais vous commencerez par réfléchir à la manière d'effectuer cette modification. Pensez à la première étape, dans laquelle vous devez stocker des valeurs.

## <a name="to-add-multiplication-and-division-problems"></a>Pour ajouter des problèmes de multiplication et de division

1.  Ajoutez quatre variables de type entier supplémentaires au formulaire.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

2.  Comme vous l'avez fait auparavant, modifiez la méthode `StartTheQuiz()` pour renseigner les problèmes de multiplication et de division avec des nombres aléatoires.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3.  Modifiez la méthode `CheckTheAnswer()` afin qu'elle vérifie également les problèmes de multiplication et de division.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Vous ne pouvez pas entrer aisément les signes de multiplication (×) et de division (÷) à l'aide du clavier, si bien que Visual C# et Visual Basic acceptent un astérisque (*) pour la multiplication et une barre oblique (/) pour la division.

4.  Modifiez la dernière partie du gestionnaire d'événements <xref:System.Windows.Forms.Timer.Tick> du minuteur afin que la réponse correcte s'affiche une fois le délai écoulé.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5.  Enregistrez et exécutez votre programme.

     Les personnes interrogées doivent résoudre quatre problèmes pour terminer le questionnaire, comme le montre l'illustration ci-dessous.

     ![Questionnaire mathématique avec quatre problèmes](../ide/media/express_finishedquiz.png)
**Questionnaire mathématique** avec quatre problèmes

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

-   Pour passer à l’étape suivante du tutoriel, consultez [Étape 8 : Personnaliser le questionnaire](../ide/step-8-customize-the-quiz.md).

-   Pour revenir à l’étape précédente du tutoriel, consultez [Étape 6 : ajouter un problème de soustraction](../ide/step-6-add-a-subtraction-problem.md).
