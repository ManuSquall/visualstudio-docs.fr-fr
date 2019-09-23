---
title: 'Étape 4 : Ajouter la méthode CheckTheAnswer()'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c9ff51d8193ebc8c1ca264a334cdd3f1fb7401b
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118921"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Étape 4 : Ajouter la méthode CheckTheAnswer()

Dans la quatrième partie de ce didacticiel, vous allez écrire une méthode, `CheckTheAnswer()`, permettant de déterminer si les réponses aux problèmes mathématiques sont correctes. Cette rubrique fait partie d'une série de didacticiels sur les concepts de codage de base. Pour obtenir une vue d’ensemble du tutoriel, consultez [Tutoriel 2 : Créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Cette rubrique fait partie d'une série de didacticiels sur les concepts de codage de base.
> - Pour obtenir une vue d’ensemble du tutoriel, consultez [Tutoriel 2 : Créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Pour télécharger une version complète du code, consultez l' [exemple complet de didacticiels mathématiques](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-verify-whether-the-answers-are-correct"></a>Pour vérifier si les réponses sont correctes

> [!NOTE]
> Si vous programmez en Visual Basic, vous utiliserez le mot clé `Function` à la place du mot clé `Sub` habituel, car cette méthode retourne une valeur. En effet, contrairement aux procédures Function, les procédures Sub ne retournent aucune valeur.

1. Ajoutez la méthode `CheckTheAnswer()`.

     Quand cette méthode est appelée, elle ajoute les valeurs d’addend1 et d’addend2, puis compare le résultat à la valeur dans le contrôle <xref:System.Windows.Forms.NumericUpDown> de somme. Si les valeurs sont égales, la méthode retourne la valeur `true`. Dans le cas contraire, la méthode retourne la valeur `false`. Votre code doit ressembler à ce qui suit.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     > [!IMPORTANT]
     > Utilisez le contrôle de langage de programmation en haut à droite de cette page pour afficher C# l’extrait de code ou le Visual Basic extrait de code.<br><br>![Contrôle du langage de programmation pour Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Vous vérifierez ensuite la réponse en mettant à jour le code dans la méthode, afin que le gestionnaire d'événements <xref:System.Windows.Forms.Timer.Tick> du minuteur appelle la nouvelle méthode `CheckTheAnswer()`.

2. Ajoutez le code suivant dans l'instruction `if else`.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Si la réponse est correcte, `CheckTheAnswer()` retourne `true`. Le gestionnaire d’événements arrête le minuteur, affiche un message de félicitations, puis rend le bouton **Démarrer** à nouveau disponible. Dans le cas contraire, le questionnaire continue.

3. Enregistrez le programme, exécutez-le, démarrez un questionnaire et fournissez une réponse correcte au problème d'addition.

    > [!NOTE]
    > Lorsque vous écrivez la réponse, sélectionnez la valeur par défaut avant de commencer à écrire votre réponse, ou supprimez le zéro manuellement. Vous corrigerez ce comportement ultérieurement dans ce didacticiel.

     Quand vous fournissez une réponse correcte, une boîte de message s’ouvre, le bouton **Démarrer** devient disponible et le minuteur s’arrête.

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du didacticiel, **consultez [étape 5 : Ajoutez des gestionnaires d’événements Enter pour les contrôles](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)** NumericUpDown.

- Pour revenir à l’étape précédente du tutoriel, consultez [Étape 3 : Ajouter un temporisateur](../ide/step-3-add-a-countdown-timer.md).
