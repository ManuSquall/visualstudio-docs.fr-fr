---
title: 'Étape 5 : Ajouter des gestionnaires d’événements Enter pour les contrôles NumericUpDown'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 45a99a5d-c881-4298-b74d-adb481dec5ee
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 393e43a44045f4551fbf567f1de037e77dbae00e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53846897"
---
# <a name="step-5-add-enter-event-handlers-for-the-numericupdown-controls"></a>Étape 5 : Ajouter des gestionnaires d’événements Enter pour les contrôles NumericUpDown
Dans la cinquième partie de ce tutoriel, vous allez ajouter des gestionnaires d'événements <xref:System.Windows.Forms.Control.Enter> pour simplifier légèrement la saisie des réponses aux problèmes du questionnaire. Ce code sélectionne et efface la valeur actuelle de chaque contrôle <xref:System.Windows.Forms.NumericUpDown> dès que la personne répondant au questionnaire le choisit et commence à entrer une autre valeur.

> [!NOTE]
>  Cette rubrique fait partie d'une série de didacticiels sur les concepts de codage de base. Pour obtenir une vue d’ensemble du tutoriel, consultez [Tutoriel 2 : Créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-the-default-behavior"></a>Pour vérifier le comportement par défaut

1.  Exécutez votre programme et démarrez le questionnaire.

     Dans le contrôle **NumericUpDown** du problème d’addition, le curseur clignote en regard de **0** (zéro).

2.  Entrez **3** et notez que le contrôle affiche **30**.

3.  Entrez **5** et notez que **350** apparaît, mais prend la valeur **100** après une seconde.

     Avant de résoudre ce problème, réfléchissez à ses causes. Pourquoi **0** n'a-t-il pas disparu lorsque vous avez entré **3** et pourquoi **350** est-il devenu **100**, mais pas immédiatement ?

     Ce comportement peut sembler étrange, mais il est cohérent en tenant compte de la logique du code. Quand vous choisissez le bouton **Démarrer**, la valeur **False** est affectée à sa propriété **Enabled**, si bien que le bouton apparaît grisé et ne peut pas être sélectionné. Votre programme modifie la sélection actuelle (focus) du contrôle dont la valeur TabIndex suivante est la plus faible, ce qui correspond au contrôle NumericUpDown pour le problème d'addition. Lorsque vous utilisez la touche **Tab** pour accéder à un contrôle NumericUpDown, le curseur est automatiquement positionné au début du contrôle, et par conséquent, les nombres que vous entrez apparaissent à partir de la gauche et non de la droite. Quand vous spécifiez un nombre qui est plus élevé que la valeur de la propriété **MaximumValue**, définie à 100, le nombre que vous entrez est remplacé par la valeur de cette propriété.

## <a name="to-add-an-enter-event-handler-for-a-numericupdown-control"></a>Pour ajouter un gestionnaire d'événements Enter pour un contrôle NumericUpDown

1.  Sélectionnez le premier contrôle **NumericUpDown** (nommé « somme ») du formulaire, puis, dans la boîte de dialogue **Propriétés**, sélectionnez l’icône **Événements** de la barre d’outils.

     L’onglet **Événements** de la boîte de dialogue **Propriétés** affiche tous les événements auxquels vous pouvez répondre (que vous pouvez gérer) pour l’élément que vous sélectionnez sur le formulaire. Comme vous avez choisi le contrôle NumericUpDown, tous les événements répertoriés s'y appliquent.

2.  Sélectionnez l’événement **Enter**, entrez `answer_Enter`, puis choisissez la touche **Entrée**.

     ![Boîte de dialogue Propriétés](../ide/media/express_answerenter.png)
Boîte de dialogue **Propriétés**

     Vous venez d’ajouter un gestionnaire d’événements Enter pour le contrôle NumericUpDown de somme et vous avez nommé le gestionnaire **answer_Enter**.

3.  Dans la méthode du gestionnaire d’événements **answer_Enter**, ajoutez le code suivant.

     [!code-vb[VbExpressTutorial3Step5_6#11](../ide/codesnippet/VisualBasic/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#11](../ide/codesnippet/CSharp/step-5-add-enter-event-handlers-for-the-numericupdown-controls_1.cs)]

     Ce code peut sembler complexe, mais vous le comprendrez si vous l'examinez de manière détaillée. Commencez par analyser le haut de la méthode : `object sender` en C# ou `sender As System.Object` en Visual Basic. Ce paramètre désigne l'objet dont l'événement se déclenche, appelé l'expéditeur. Dans ce cas, l'objet expéditeur est le contrôle NumericUpDown. Ainsi, dans la première ligne de la méthode, vous indiquez que l'expéditeur n'est pas seulement un objet générique, mais plus précisément un contrôle NumericUpDown. (Chaque contrôle NumericUpDown est un objet, mais chaque objet n'est pas un contrôle NumericUpDown.) Le contrôle NumericUpDown est nommé **answerBox** dans cette méthode, car il sera utilisé pour tous les contrôles NumericUpDown du formulaire et pas seulement pour le contrôle NumericUpDown de somme. Comme vous déclarez la variable answerBox dans cette méthode, sa portée s'applique uniquement à cette méthode. En d'autres termes, la variable peut être utilisée uniquement dans cette méthode.

     La ligne suivante vérifie si l’objet answerBox a été converti (cast) correctement en contrôle NumericUpDown. Si la conversion était infructueuse, la variable aurait la valeur `null` (C#) ou `Nothing` (Visual Basic). La troisième ligne obtient la longueur de la réponse qui apparaît dans le contrôle NumericUpDown et la quatrième ligne sélectionne la valeur actuelle dans le contrôle en fonction de cette longueur. Maintenant, lorsque la personne répondant au questionnaire choisit le contrôle, Visual Studio déclenche cet événement, ce qui entraîne la sélection de la réponse actuelle. Dès que la personne interrogée commence à entrer une réponse différente, la réponse précédente est effacée et remplacée par la nouvelle réponse.

4.  Dans le **Concepteur Windows Forms**, choisissez le contrôle **NumericUpDown** de différence.

5.  Dans la page **Événements** de la boîte de dialogue **Propriétés**, faites défiler l’écran jusqu’à l’événement **Enter**, choisissez la flèche déroulante à la fin de la ligne, puis choisissez le gestionnaire d’événements `answer_Enter` que vous venez d’ajouter.

6.  Répétez l'étape précédente pour les contrôles NumericUpDown de produit et de quotient.

7.  Enregistrez votre programme, puis exécutez-le.

     Quand vous choisissez un contrôle **NumericUpDown**, la valeur existante est automatiquement activée puis désactivée lorsque vous commencez à entrer une autre valeur.

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

-   Pour passer à l’étape suivante du tutoriel, consultez [Étape 6 : Ajouter un problème de soustraction](../ide/step-6-add-a-subtraction-problem.md).

-   Pour revenir à l’étape précédente du tutoriel, consultez [Étape 4 : Ajouter la méthode CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).
