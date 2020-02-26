---
title: 'Étape 5 : ajouter des références d’étiquettes'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de89d7194425e1a8cba9e11f2734372d80b256b3
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579330"
---
# <a name="step-5-add-label-references"></a>Étape 5 : ajouter des références d’étiquettes
Le programme doit effectuer le suivi des contrôles d’étiquette choisis par le joueur. Pour le moment, le programme indique l'ensemble des étiquettes choisies par le joueur. Mais nous allons changer cela. Une fois que le joueur a choisi le premier contrôle d'étiquette, le programme doit afficher son icône. Une fois que le joueur a choisi le deuxième contrôle d'étiquette, le programme doit afficher brièvement les deux icônes, puis les masquer à nouveau. Votre programme vérifiera à présent quel contrôle d'étiquette le joueur a choisi en premier et en deuxième à l'aide de *variables de référence*.

## <a name="to-add-label-references"></a>Pour ajouter des références aux contrôles Label

1. Pour ajouter des références aux contrôles Label dans votre formulaire, utilisez le code suivant.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     > [!IMPORTANT]
     > Utilisez le contrôle de langage de programmation en haut à droite de cette page pour afficher C# l’extrait de code ou le Visual Basic extrait de code.<br><br>contrôle du langage de programmation ![pour Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Ces variables de référence sont identiques aux instructions que vous avez utilisées avant pour ajouter des objets (comme les objets <xref:System.Windows.Forms.Timer>, <xref:System.Collections.Generic.List%601> et <xref:System.Random> ) à votre formulaire. Toutefois, ces instructions n'entraînent pas l'affichage de deux contrôles d'étiquette supplémentaires dans le formulaire étant donné qu'il n'existe aucun `new` mot-clé dans l'une ou l'autre des deux instructions. Sans le `new` mot-clé, aucun objet n'est créé. C'est la raison pour laquelle `firstClicked` et `secondClicked` sont appelées variables de référence : elles sont uniquement chargées de suivre (ou de référencer) les objets d’étiquette.

     Lorsqu’une variable n’effectue pas le suivi d’un objet, elle est définie sur une valeur réservée spéciale C# : `null` dans et `Nothing` dans Visual Basic. Au démarrage du programme, `firstClicked` et `secondClicked` ont donc la valeur `null` ou `Nothing`, ce qui signifie que les variables n'effectuent aucun suivi.

2. Modifiez votre gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> pour qu’il utilise la nouvelle variable de référence `firstClicked`. Supprimez la dernière instruction dans la méthode du gestionnaire d'événements `label_Click()` (`clickedLabel.ForeColor = Color.Black;`) et remplacez-la par l'instruction `if` suivante. (Veillez à inclure le commentaire et la totalité de l'instruction `if`.)

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Enregistrez et exécutez votre programme. Choisissez l'un des contrôles d'étiquette, et son icône s'affiche.

4. Choisissez le contrôle d'étiquette suivant, et notez que rien ne se passe. Le programme effectue déjà le suivi du premier contrôle Label choisi par le joueur, donc `firstClicked` n’est pas égal à C# `null` dans ou `Nothing` dans Visual Basic. Lorsque votre instruction `if` vérifie si `firstClicked` est égal à `null` ou `Nothing`, elle découvre que ce n'est pas le cas et n'exécute pas les instructions dans l'instruction `if`. Ainsi, seule la première icône choisie devient noire et les autres icônes sont invisibles, comme illustré dans l’image suivante.

     ![Jeu de combinaisons affichant une icône](../ide/media/express_tut4step5.png)<br/>
***Jeu de combinaisons*** *avec une icône*

     Vous allez résoudre cette situation à l'étape suivante du didacticiel en ajoutant un contrôle **Minuterie**.

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du didacticiel, consultez **[étape 6 : ajouter une minuterie](../ide/step-6-add-a-timer.md)** .

- Pour revenir à l'étape précédente du tutoriel, consultez [Étape 4 : ajouter un gestionnaire d'événements Click à chaque étiquette](../ide/step-4-add-a-click-event-handler-to-each-label.md).
