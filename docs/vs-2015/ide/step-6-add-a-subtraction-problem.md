---
title: 'Étape 6 : ajouter un problème de soustraction | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 793204bf4a08d09d7ce6e48e37254dd311ac6a08
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229240"
---
# <a name="step-6-add-a-subtraction-problem"></a>Étape 6 : ajouter un problème de soustraction
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans la sixième partie de ce didacticiel, vous allez ajouter un problème de soustraction et apprendre à effectuer les tâches suivantes :  
  
-   Stocker les valeurs de soustraction.  
  
-   Générer des nombres aléatoires pour le problème (et vérifier que la réponse est comprise entre 0 et 100).  
  
-   Mettre à jour la méthode qui vérifie les réponses afin qu'elle vérifie également le nouveau problème de soustraction.  
  
-   Mettre à jour le gestionnaire d'événements Tick de votre minuterie pour qu'il remplisse la réponse correcte lorsque le temps est écoulé.  
  
### <a name="to-add-a-subtraction-problem"></a>Pour ajouter un problème de soustraction  
  
1.  Ajoutez deux variables de type entier à votre formulaire pour le problème de soustraction, entre les variables de type entier du problème d'addition et la minuterie. Le code doit se présenter comme suit.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#12](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#12)]
     [!code-vb[VbExpressTutorial3Step5_6#12](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#12)]  
  
     Les noms des nouvelles variables de type entier (**minuend** et **subtrahend**) ne sont pas des termes de programmation. Ce sont des noms généralement utilisés en arithmétique pour désigner le nombre à retrancher (subtrahend, ou diminuteur en français) et le nombre duquel le diminuteur est soustrait (minuend, ou diminuende en français). La différence correspond à minuend moins subtrahend. Vous pourriez utiliser d'autres noms, étant donné que votre programme ne requiert aucun nom spécifique pour les variables, les contrôles, les composants ou les méthodes. Vous devez suivre des règles, par exemple ne pas commencer les noms par des chiffres, mais plutôt recourir à des noms tels que x1, x2, x3 et x4. Toutefois, les noms génériques rendent le code difficile à lire et les problèmes quasiment impossible à localiser. Pour faire en sorte que les noms des variables soient uniques et conviviaux, vous utiliserez les noms traditionnels pour la multiplication (multiplicande x multiplicateur = produit) et la division (dividende ÷ diviseur = quotient) plus tard dans ce didacticiel.  
  
     Vous modifierez ensuite la méthode `StartTheQuiz()` permettant de fournir des valeurs aléatoires pour le problème de soustraction.  
  
2.  Ajoutez le code suivant après le commentaire « Fill in the subtraction problem » (« Remplissage du problème de soustraction »).  
  
     [!code-csharp[VbExpressTutorial3Step5_6#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#13)]
     [!code-vb[VbExpressTutorial3Step5_6#13](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#13)]  
  
     Pour éviter les réponses négatives dans le cadre d'un problème de soustraction, ce code utilise la méthode `Next()` de la classe `Random` un peu différemment que pour le problème d'addition. Lorsque vous attribuez deux valeurs à la méthode `Next()`, elle choisit un nombre aléatoire qui est supérieur ou égal à la première valeur, mais inférieur à la deuxième. Le code suivant choisit un nombre aléatoire entre 1 et 100 et le stocke dans la variable minuend.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#21](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#21)]
     [!code-vb[VbExpressTutorial3Step5_6#21](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#21)]  
  
     Vous pouvez appeler la méthode `Next()` de la classe `Random`, que vous avez nommée « randomizer » précédemment dans ce didacticiel, de plusieurs façons. Les méthodes que vous appelez de plusieurs façons sont désignées comme étant surchargées, et vous pouvez utiliser IntelliSense pour les explorer. Examinez à nouveau l'info-bulle de la fenêtre IntelliSense pour la méthode `Next()`.  
  
     ![Info-bulle de la fenêtre Intellisense](../ide/media/express-overloads.png "Express_Overloads")  
Info-bulle de la fenêtre Intellisense  
  
     L’info-bulle affiche **(+ 2 surcharge(s))**, ce qui signifie que vous pouvez appeler la méthode `Next()` de deux manières différentes. Les surcharges contiennent des nombres ou des types d’arguments leur permettant de fonctionner un peu différemment les unes des autres. Par exemple, une méthode peut prendre un argument entier unique, alors qu'une de ses surcharges peut prendre un entier et une chaîne. Choisissez la surcharge appropriée en fonction de ce que vous souhaitez qu'elle fasse. Lorsque vous ajoutez du code à la méthode `StartTheQuiz()`, plus d'informations apparaissent dans la fenêtre IntelliSense dès que vous entrez `randomizer.Next(`. Choisissez les flèches vers le haut et vers le bas pour parcourir les surcharges, comme indiqué dans l'illustration suivante.  
  
     ![Surcharge pour la méthode Next&#40;&#41; dans IntelliSense](../ide/media/express-nextoverload.png "Express_NextOverload")  
Surcharge pour la méthode Next() dans IntelliSense  
  
     Dans ce cas, vous souhaitez choisir la dernière surcharge, car vous pouvez spécifier les valeurs minimales et maximales.  
  
3.  Modifiez la méthode `CheckTheAnswer()` pour vérifier si la réponse à la soustraction est correcte.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial3Step5_6#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#14)]  
  
     En Visual C#, `&&` correspond à l'opérateur `logical and`. En Visual Basic, l'opérateur équivalent est `AndAlso`. Ces opérateurs indiquent « si la somme de addend1 et addend2 est égale à la valeur de la somme NumericUpDown, et si minuend moins subtrahend est égal à la valeur de difference NumericUpDown ». La méthode `CheckTheAnswer()` retourne `true` si les réponses aux problèmes d'addition et de soustraction sont toutes les deux correctes.  
  
4.  Remplacez la dernière partie du gestionnaire d'événements Tick du minuteur par le code suivant afin que la réponse correcte s'affiche une fois le délai écoulé.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#22](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#22)]
     [!code-vb[VbExpressTutorial3Step5_6#22](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#22)]  
  
5.  Enregistrez et exécutez votre code.  
  
     Votre programme inclut un problème de soustraction, comme le présente l'illustration suivante.  
  
     ![Questionnaire mathématique avec problème de soustraction](../ide/media/express-addsubtract.png "Express_AddSubtract")  
Questionnaire mathématique avec problème de soustraction  
  
### <a name="to-continue-or-review"></a>Pour continuer ou examiner  
  
-   Pour passer à l’étape suivante du didacticiel, consultez [Étape 7 : ajouter des problèmes de multiplication et de division](../ide/step-7-add-multiplication-and-division-problems.md).  
  
-   Pour revenir à l’étape précédente du didacticiel, consultez [Étape 5 : ajouter des gestionnaires d’événements Enter pour les contrôles NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).



