---
title: Écrire du code pour des boutons supplémentaires et une case à cocher
description: Apprenez à écrire du code pour des boutons supplémentaires et une case à cocher dans le didacticiel créer une visionneuse d’images.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 095c402b54e32dbd0839ff89def83d64d1522f4a
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296558"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Étape 10 : Écrire du code pour des boutons supplémentaires et une case à cocher

Vous êtes maintenant prêt à générer les quatre autres méthodes. Vous pourriez copier et coller ce code, mais pour tirer pleinement parti de ce didacticiel, il serait préférable que vous tapiez le code et que vous utilisiez IntelliSense.

Ce code ajoute des fonctionnalités aux boutons que vous avez ajoutés précédemment. Sans le code, les boutons n'ont aucun effet. Les boutons utilisent un code dans leurs événements <xref:System.Windows.Forms.Control.Click> (et la case à cocher utilise l'événement <xref:System.Windows.Forms.CheckBox.CheckedChanged>) pour effectuer différentes opérations lorsque vous activez les contrôles. Par exemple, l' `clearButton_Click` événement ( `ClearButton_Click` ou), qui s’active quand vous choisissez le bouton **effacer l’image** , efface l’image actuelle en affectant à sa propriété **image** la **valeur null** (ou, **Nothing**). Chaque événement dans le code inclut des commentaires qui expliquent la fonction du code.

> [!TIP]
> N'oubliez pas de toujours commenter votre code. Les commentaires sont des informations qu'une personne peut lire, et il est toujours utile de prendre un peu de temps pour détailler les objectifs de votre code. Tout ce qui se trouve sur une ligne de commentaire est ignoré par l’application. En C#, vous commentez une ligne en tapant deux barres obliques au début (//), et dans Visual Basic vous commentez une ligne en commençant par un guillemet simple (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Comment écrire du code pour des boutons supplémentaires et une case à cocher

Ajoutez le code suivant à votre fichier de code **Form1** (*Form1.cs* ou *Form1.vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs" id="Snippet2":::

  :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb" id="Snippet2":::

> [!NOTE]
> Votre code risque de ne pas afficher les lettres « la casse mixte ».

## <a name="next-steps"></a>Étapes suivantes

* Pour passer à l’étape suivante du didacticiel, consultez **[étape 11 : exécuter votre application et essayer d’autres fonctionnalités](../ide/step-11-run-your-program-and-try-other-features.md)**.

* Pour revenir à l’étape précédente du tutoriel, consultez [Étape 9 : examiner, commenter et tester votre code](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Voir aussi

* [Didacticiel 2 : créer un questionnaire mathématique chronométré](tutorial-2-create-a-timed-math-quiz.md)
* [Didacticiel 3 : créer un jeu de combinaisons](tutorial-3-create-a-matching-game.md)
