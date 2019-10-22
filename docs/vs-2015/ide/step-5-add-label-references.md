---
title: 'Étape 5 : ajouter des références de contrôles Label | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 51512c80c96ef82835ce38c36e3643261ba84231
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671743"
---
# <a name="step-5-add-label-references"></a>Étape 5 : ajouter des références de contrôles Label
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le programme doit effectuer le suivi des contrôles d'étiquette que le joueur a choisis. Pour le moment, le programme indique l'ensemble des étiquettes choisies par le joueur. Mais nous allons changer cela. Une fois que le joueur a choisi le premier contrôle d'étiquette, le programme doit afficher son icône. Une fois que le joueur a choisi le deuxième contrôle d'étiquette, le programme doit afficher brièvement les deux icônes, puis les masquer à nouveau. Votre programme vérifiera à présent quel contrôle d'étiquette le joueur a choisi en premier et en deuxième à l'aide de *variables de référence*.

### <a name="to-add-label-references"></a>Pour ajouter des références aux contrôles Label

1. Pour ajouter des références aux contrôles Label dans votre formulaire, utilisez le code suivant.

     [!code-csharp[VbExpressTutorial4Step5#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial4Step5#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#5)]

     Ces variables de référence sont identiques aux instructions que vous avez utilisées avant pour ajouter des objets (comme les objets `Timer`, `List` et `Random` ) à votre formulaire. Toutefois, ces instructions n'entraînent pas l'affichage de deux contrôles d'étiquette supplémentaires dans le formulaire étant donné qu'il n'existe aucun `new` mot-clé dans l'une ou l'autre des deux instructions. Sans le `new` mot-clé, aucun objet n'est créé. C'est la raison pour laquelle `firstClicked` et `secondClicked` sont appelées « variables de référence » : elles sont uniquement chargées de suivre (ou de référencer) les objets `Label`.

     Lorsqu'une variable n'effectue pas le suivi d'un objet, elle est définie sur une valeur spéciale : `null` en Visual C# et `Nothing` en Visual Basic. Au démarrage du programme, `firstClicked` et `secondClicked` ont donc la valeur `null` ou `Nothing`, ce qui signifie que les variables n'effectuent aucun suivi.

2. Modifiez votre gestionnaire d'événements Click pour qu'il utilise la nouvelle variable de référence `firstClicked`. Supprimez la dernière instruction dans la méthode du gestionnaire d'événements `label_Click()` (`clickedLabel.ForeColor = Color.Black;`) et remplacez-la par l'instruction `if` suivante. (Veillez à inclure le commentaire et la totalité de l'instruction `if`.)

     [!code-csharp[VbExpressTutorial4Step5#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial4Step5#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb#6)]

3. Enregistrez et exécutez votre programme. Choisissez l'un des contrôles d'étiquette, et son icône s'affiche.

4. Choisissez le contrôle d'étiquette suivant, et notez que rien ne se passe. Le programme effectue déjà le suivi du premier contrôle choisissez que le joueur a choisi et donc `firstClicked` n'est pas égal à `null` en Visual C# ou `Nothing` en Visual Basic. Lorsque votre instruction `if` vérifie si `firstClicked` est égal à `null` ou `Nothing`, elle découvre que ce n'est pas le cas et n'exécute pas les instructions dans l'instruction `if`. Par conséquent, seule la première icône que le joueur a choisie devient noire et les autres restent invisibles, comme indiqué dans l'image suivante.

     ![Jeu de combinaisons avec une icône](../ide/media/express-tut4step5.png "Express_Tut4Step5") Jeu de combinaisons avec une icône

     Vous allez résoudre cette situation à l'étape suivante du didacticiel en ajoutant un contrôle **Minuterie**.

### <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du didacticiel, consultez [Étape 6 : ajouter une minuterie](../ide/step-6-add-a-timer.md).

- Pour revenir à l'étape précédente du didacticiel, consultez [Étape 4 : ajouter un gestionnaire d'événements Click à chaque contrôle Label](../ide/step-4-add-a-click-event-handler-to-each-label.md).
