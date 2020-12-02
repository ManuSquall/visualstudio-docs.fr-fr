---
title: 'Étape 4 : Ajouter la méthode CheckTheAnswer()'
description: Découvrez comment écrire une méthode méthode CheckTheAnswer () pour déterminer si les réponses aux problèmes mathématiques sont correctes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a1d9d22363aa26628d122b451c51fb7d1df29fbe
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480588"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Étape 4 : Ajouter la méthode CheckTheAnswer()

Dans la quatrième partie de ce didacticiel, vous allez écrire une méthode, `CheckTheAnswer()`, permettant de déterminer si les réponses aux problèmes mathématiques sont correctes. Cette rubrique fait partie d'une série de didacticiels sur les concepts de codage de base. Pour obtenir une vue d’ensemble du didacticiel, consultez [didacticiel 2 : créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Cette rubrique fait partie d'une série de didacticiels sur les concepts de codage de base. Pour obtenir une vue d’ensemble du didacticiel, consultez [didacticiel 2 : créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-whether-the-answers-are-correct"></a>Pour vérifier si les réponses sont correctes

> [!NOTE]
> Si vous programmez en Visual Basic, vous utiliserez le mot clé `Function` à la place du mot clé `Sub` habituel, car cette méthode retourne une valeur. En effet, contrairement aux procédures Function, les procédures Sub ne retournent aucune valeur.

1. Ajoutez la méthode `CheckTheAnswer()`. Cette méthode doit être alignée sur les autres méthodes que vous avez effectuées, telles que `StartTheQuiz()` .

     Quand cette méthode est appelée, elle ajoute les valeurs d’addend1 et d’addend2, puis compare le résultat à la valeur dans le contrôle <xref:System.Windows.Forms.NumericUpDown> de somme. Si les valeurs sont égales, la méthode retourne la valeur `true`. Dans le cas contraire, la méthode retourne la valeur `false`. Votre code doit ressembler à ce qui suit.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Vous vérifierez ensuite la réponse en mettant à jour le code dans la méthode, afin que le gestionnaire d'événements <xref:System.Windows.Forms.Timer.Tick> du minuteur appelle la nouvelle méthode `CheckTheAnswer()`.

2. Ajoutez le code suivant à l' `if else` instruction dans la `Timer1_Tick()` méthode, afin que la minuterie s’arrête lorsque l’utilisateur obtient le droit de réponse.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Si la réponse est correcte, `CheckTheAnswer()` retourne `true`. Le gestionnaire d’événements arrête le minuteur, affiche un message de félicitations, puis rend le bouton **Démarrer** à nouveau disponible. Dans le cas contraire, le questionnaire continue.

3. Enregistrez le programme, exécutez-le, démarrez un questionnaire et fournissez une réponse correcte au problème d'addition.

    > [!NOTE]
    > Lorsque vous écrivez la réponse, sélectionnez la valeur par défaut avant de commencer à écrire votre réponse, ou supprimez le zéro manuellement. Vous corrigerez ce comportement ultérieurement dans ce didacticiel.

     Quand vous fournissez une réponse correcte, une boîte de message s’ouvre, le bouton **Démarrer** devient disponible et le minuteur s’arrête.

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du didacticiel, consultez **[étape 5 : ajouter des gestionnaires d’événements Enter pour les contrôles NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)**.

- Pour revenir à l’étape précédente du tutoriel, consultez [Étape 3 : ajouter un compte à rebours](../ide/step-3-add-a-countdown-timer.md).
