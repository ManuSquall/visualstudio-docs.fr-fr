---
title: 'Étape 10 : écrire du code pour des boutons supplémentaires et une case à cocher'
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0dc7281b51d0efe0d19020df6a154e332ad9bb0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579440"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Étape 10 : écrire du code pour des boutons supplémentaires et une case à cocher

Vous êtes maintenant prêt à générer les quatre autres méthodes. Vous pourriez copier et coller ce code, mais pour tirer pleinement parti de ce didacticiel, il serait préférable que vous tapiez le code et que vous utilisiez IntelliSense.

Ce code ajoute des fonctionnalités aux boutons que vous avez ajoutés précédemment. Sans le code, les boutons n'ont aucun effet. Les boutons utilisent un code dans leurs événements <xref:System.Windows.Forms.Control.Click> (et la case à cocher utilise l'événement <xref:System.Windows.Forms.CheckBox.CheckedChanged>) pour effectuer différentes opérations lorsque vous activez les contrôles. Par exemple, `clearButton_Click` l’événement (ou) `ClearButton_Click`qui s’active lorsque vous choisissez le bouton **Effacer l’image,** efface l’image actuelle en définissant sa propriété **Image** à **nulle** (ou, **rien**). Chaque événement dans le code inclut des commentaires qui expliquent la fonction du code.

> [!TIP]
> N'oubliez pas de toujours commenter votre code. Les commentaires sont des informations qu'une personne peut lire, et il est toujours utile de prendre un peu de temps pour détailler les objectifs de votre code. Tout sur une ligne de commentaire est ignoré par l’application. Dans C, vous commentez une ligne en tapant deux barres obliques avant au début (//), et dans Visual Basic vous commentez une ligne en commençant par une seule marque de de devis (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Comment écrire du code pour les boutons supplémentaires et une case à cocher

Ajoutez le code suivant à votre fichier de code **Form1** (*Form1.cs* ou *Form1.vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Votre code pourrait ne pas afficher les lettres "camelCase".

## <a name="next-steps"></a>Étapes suivantes

* Pour passer à l’étape suivante tutoriel, voir **[Étape 11: Exécuter votre application et essayer d’autres fonctionnalités](../ide/step-11-run-your-program-and-try-other-features.md)**.

* Pour revenir à l’étape précédente du tutoriel, consultez [Étape 9 : examiner, commenter et tester votre code](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Voir aussi

* [Tutorial 2: Créer un quiz de mathématiques chronométré](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Créer un jeu correspondant](tutorial-3-create-a-matching-game.md)
