---
title: 'Tutoriel 2 : créer un questionnaire mathématique chronométré'
ms.date: 10/16/2019
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b1f3620ef462228ff6a3461f44019e9c515a1c0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579304"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Tutoriel 2 : créer un questionnaire mathématique chronométré

Dans ce didacticiel, vous générez un questionnaire dans lequel la personne interrogée doit résoudre quatre problèmes arithmétiques aléatoires dans un délai imparti.

> [!NOTE]
> Ce tutoriel couvre à la fois C et Visual Basic, alors concentrez-vous sur les informations spécifiques au langage de programmation que vous utilisez.

Ce tutoriel vous guide à travers les tâches suivantes:

- Générer des nombres aléatoires à l'aide de la classe <xref:System.Random>.

- Déclencher des événements à une heure spécifique à l’aide d’un contrôle <xref:System.Windows.Forms.Timer>.

- Contrôler le flux d'un programme à l'aide d'instructions `if else`.

- Effectuer des opérations arithmétiques de base dans le code.

Lorsque vous avez terminé, votre quiz ressemblera à la capture d’écran suivante, sauf avec des nombres différents:

![Questionnaire mathématique avec quatre problèmes](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Liens de tutoriels

|Intitulé|Description|
|-----------|-----------------|
|[Étape 1 : Créez un projet et ajoutez des étiquettes à votre formulaire](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Commencez par créer le projet, modifier ses propriétés et ajouter des contrôles `Label`.|
|[Étape 2 : créer un problème d’addition aléatoire](../ide/step-2-create-a-random-addition-problem.md)|Créez un problème d'addition et utilisez la classe `Random` pour générer des nombres aléatoires.|
|[Étape 3 : Ajouter une minuterie de compte à rebours](../ide/step-3-add-a-countdown-timer.md)|Ajoutez un temporisateur pour que le questionnaire soit chronométré.|
|[Étape 4 : ajouter la méthode CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Ajoutez une méthode pour vérifier si la personne interrogée a fourni une réponse correcte au problème.|
|[Étape 5 : Ajoutez des gestionnaires d’événements Enter pour les contrôles NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Ajoutez des gestionnaires d'événements pour faciliter le déroulement du questionnaire.|
|[Étape 6 : Ajouter un problème de soustraction](../ide/step-6-add-a-subtraction-problem.md)|Ajoutez un problème de soustraction qui génère des nombres aléatoires, utilise le minuteur et recherche les réponses correctes.|
|[Étape 7 : Ajouter la multiplication et les problèmes de division](../ide/step-7-add-multiplication-and-division-problems.md)|Ajoutez des problèmes de multiplication et de division qui génèrent des nombres aléatoires, utilisent le minuteur et recherchent les réponses correctes.|
|[Étape 8 : Personnalisez le quiz](../ide/step-8-customize-the-quiz.md)|Essayez d’autres fonctionnalités, telles que la modification des couleurs et l’ajout d’une aide.|

Il ya aussi d’excellentes ressources d’apprentissage vidéo gratuit à votre disposition. Pour en savoir plus sur la programmation dans le domaine de la programmation, consultez [les principes fondamentaux de CMD : Développement pour les débutants absolus.](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners) Pour en savoir plus sur la programmation en Visual Basic, consultez [Notions de base de Visual Basic : développement pour grands débutants](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Étapes suivantes

Pour commencer le tutoriel, commencez par **[l’étape 1: Créer un projet et ajouter des étiquettes à votre formulaire](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)**.

## <a name="see-also"></a>Voir aussi

* [Plus de tutoriels C](/visualstudio/get-started/csharp/)
* [Tutoriels Visual Basic](/visualstudio/get-started/visual-basic/)
* [Tutoriels CMD](/cpp/get-started/tutorial-console-cpp)
