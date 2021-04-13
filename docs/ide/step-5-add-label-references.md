---
title: 'Étape 5 : Ajouter des références aux étiquettes'
description: Découvrez comment ajouter des références à des étiquettes à votre formulaire.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 393f71c3360371122e86dc078aaa97c6963db325
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296272"
---
# <a name="step-5-add-label-references"></a>Étape 5 : Ajouter des références aux étiquettes
Le programme doit effectuer le suivi des contrôles d’étiquette choisis par le joueur. Pour le moment, le programme indique l'ensemble des étiquettes choisies par le joueur. Mais nous allons changer cela. Une fois que le joueur a choisi le premier contrôle d'étiquette, le programme doit afficher son icône. Une fois que le joueur a choisi le deuxième contrôle d'étiquette, le programme doit afficher brièvement les deux icônes, puis les masquer à nouveau. Votre programme vérifiera à présent quel contrôle d'étiquette le joueur a choisi en premier et en deuxième à l'aide de *variables de référence*.

## <a name="to-add-label-references"></a>Pour ajouter des références aux contrôles Label

1. Pour ajouter des références aux contrôles Label dans votre formulaire, utilisez le code suivant.

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet5":::

     > [!IMPORTANT]
     > Utilisez le contrôle de langage de programmation en haut à droite de cette page pour afficher l’extrait de code C# ou l’extrait de code Visual Basic.<br><br>![Contrôle du langage de programmation pour Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Ces variables de référence sont identiques aux instructions que vous avez utilisées avant pour ajouter des objets (comme les objets <xref:System.Windows.Forms.Timer>, <xref:System.Collections.Generic.List%601> et <xref:System.Random> ) à votre formulaire. Toutefois, ces instructions n'entraînent pas l'affichage de deux contrôles d'étiquette supplémentaires dans le formulaire étant donné qu'il n'existe aucun `new` mot-clé dans l'une ou l'autre des deux instructions. Sans le `new` mot-clé, aucun objet n'est créé. C'est la raison pour laquelle `firstClicked` et `secondClicked` sont appelées variables de référence : elles sont uniquement chargées de suivre (ou de référencer) les objets d’étiquette.

     Lorsqu’une variable n’effectue pas le suivi d’un objet, elle est définie sur une valeur réservée spéciale : `null` en C# et `Nothing` dans Visual Basic. Au démarrage du programme, `firstClicked` et `secondClicked` ont donc la valeur `null` ou `Nothing`, ce qui signifie que les variables n'effectuent aucun suivi.

2. Modifiez votre gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> pour qu’il utilise la nouvelle variable de référence `firstClicked`. Supprimez la dernière instruction dans la méthode du gestionnaire d'événements `label_Click()` (`clickedLabel.ForeColor = Color.Black;`) et remplacez-la par l'instruction `if` suivante. (Veillez à inclure le commentaire et la totalité de l'instruction `if`.)

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet6":::

3. Enregistrez et exécutez votre programme. Choisissez l'un des contrôles d'étiquette, et son icône s'affiche.

4. Choisissez le contrôle d'étiquette suivant, et notez que rien ne se passe. Le programme effectue déjà le suivi de la première étiquette choisie par le joueur, donc il `firstClicked` n’est pas égal à `null` en C# ou `Nothing` à Visual Basic. Lorsque votre instruction `if` vérifie si `firstClicked` est égal à `null` ou `Nothing`, elle découvre que ce n'est pas le cas et n'exécute pas les instructions dans l'instruction `if`. Ainsi, seule la première icône choisie devient noire et les autres icônes sont invisibles, comme illustré dans l’image suivante.

     ![Jeu de combinaisons affichant une icône](../ide/media/express_tut4step5.png)<br/>
***Match du jeu** _ _showing une icône *

     Vous allez résoudre cette situation à l'étape suivante du didacticiel en ajoutant un contrôle **Minuterie**.

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer à l’étape suivante du didacticiel, consultez **[étape 6 : ajouter une minuterie](../ide/step-6-add-a-timer.md)**.

- Pour revenir à l'étape précédente du tutoriel, consultez [Étape 4 : ajouter un gestionnaire d'événements Click à chaque étiquette](../ide/step-4-add-a-click-event-handler-to-each-label.md).
