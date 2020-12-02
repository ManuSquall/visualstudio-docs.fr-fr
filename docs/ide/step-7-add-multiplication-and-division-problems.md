---
title: 'Étape 7 : Ajouter des problèmes de multiplication et de division'
description: Découvrez comment ajouter des problèmes de multiplication et de division.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84dc1df79392aeefe331746c52d2fbe8dbb91e8e
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479496"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Étape 7 : Ajouter des problèmes de multiplication et de division

Dans la septième partie de ce didacticiel, vous allez ajouter des problèmes de multiplication et de division, mais vous commencerez par réfléchir à la manière d'effectuer cette modification. Pensez à la première étape, dans laquelle vous devez stocker des valeurs.

> [!NOTE]
> Cette rubrique fait partie d'une série de didacticiels sur les concepts de codage de base. Pour obtenir une vue d’ensemble du didacticiel, consultez [didacticiel 2 : créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md).

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

     Vous ne pouvez pas entrer facilement le signe de multiplication (×) et le signe de division (÷) à l’aide du clavier. par conséquent, C# et Visual Basic acceptent un astérisque (*) pour la multiplication et une barre oblique (/) pour la Division.

4. Modifiez la dernière partie du gestionnaire d'événements <xref:System.Windows.Forms.Timer.Tick> du minuteur afin que la réponse correcte s'affiche une fois le délai écoulé.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Enregistrez et exécutez votre programme.

     Les personnes interrogées doivent résoudre quatre problèmes pour terminer le questionnaire, comme le montre l'illustration ci-dessous.

     ![Questionnaire mathématique avec quatre problèmes](../ide/media/express_finishedquiz.png)<br/>
***Questionnaire mathématique** _ _with quatre problèmes *

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du didacticiel, consultez **[étape 8 : personnaliser le quiz](../ide/step-8-customize-the-quiz.md)**.

- Pour revenir à l’étape précédente du tutoriel, consultez [Étape 6 : ajouter un problème de soustraction](../ide/step-6-add-a-subtraction-problem.md).
