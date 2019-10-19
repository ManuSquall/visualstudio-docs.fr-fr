---
title: 'Étape 7 : ajouter des problèmes de multiplication et de division'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 342a27571c9ad7b6ed1586fc762b2952ba86c3db
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575159"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Étape 7 : ajouter des problèmes de multiplication et de division

Dans la septième partie de ce didacticiel, vous allez ajouter des problèmes de multiplication et de division, mais vous commencerez par réfléchir à la manière d'effectuer cette modification. Pensez à la première étape, dans laquelle vous devez stocker des valeurs.

> [!NOTE]
> Cette rubrique fait partie d'une série de didacticiels sur les concepts de codage de base.
> - Pour obtenir une vue d’ensemble du tutoriel, consultez [Tutoriel 2 : créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Pour télécharger une version complète du code, consultez l' [exemple complet de didacticiels mathématiques](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-add-multiplication-and-division-problems"></a>Pour ajouter des problèmes de multiplication et de division

1. Ajoutez quatre variables de type entier supplémentaires au formulaire.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Comme vous l'avez fait auparavant, modifiez la méthode `StartTheQuiz()` pour renseigner les problèmes de multiplication et de division avec des nombres aléatoires.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. Modifiez la méthode `CheckTheAnswer()` afin qu'elle vérifie également les problèmes de multiplication et de division.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Vous ne pouvez pas entrer facilement le signe de multiplication (×) et le signe de division (÷) à l' C# aide du clavier, donc et Visual Basic accepter un astérisque (*) pour la multiplication et une barre oblique (/) pour la Division.

4. Modifiez la dernière partie du gestionnaire d'événements <xref:System.Windows.Forms.Timer.Tick> du minuteur afin que la réponse correcte s'affiche une fois le délai écoulé.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Enregistrez et exécutez votre programme.

     Les personnes interrogées doivent résoudre quatre problèmes pour terminer le questionnaire, comme le montre l'illustration ci-dessous.

     ![Questionnaire mathématique avec quatre problèmes](../ide/media/express_finishedquiz.png)<br/>
***Questionnaire mathématique*** *avec quatre problèmes*

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du didacticiel, consultez **[Step 8 : Customize the quiz](../ide/step-8-customize-the-quiz.md)** S.

- Pour revenir à l’étape précédente du tutoriel, consultez [Étape 6 : ajouter un problème de soustraction](../ide/step-6-add-a-subtraction-problem.md).
