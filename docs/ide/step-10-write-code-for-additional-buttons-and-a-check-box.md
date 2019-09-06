---
title: 'Étape 10 : Écrire du code pour des boutons supplémentaires et une case à cocher'
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 281c98ca52b6dd18ee726e3191d47d6755fd8326
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293616"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Étape 10 : Écrire du code pour des boutons supplémentaires et une case à cocher

Vous êtes maintenant prêt à générer les quatre autres méthodes. Vous pourriez copier et coller ce code, mais pour tirer pleinement parti de ce didacticiel, il serait préférable que vous tapiez le code et que vous utilisiez IntelliSense.

Ce code ajoute des fonctionnalités aux boutons que vous avez ajoutés précédemment. Sans le code, les boutons n'ont aucun effet. Les boutons utilisent un code dans leurs événements <xref:System.Windows.Forms.Control.Click> (et la case à cocher utilise l'événement <xref:System.Windows.Forms.CheckBox.CheckedChanged>) pour effectuer différentes opérations lorsque vous activez les contrôles. Par exemple, l' `clearButton_Click` événement ( `ClearButton_Click`ou), qui s’active quand vous choisissez le bouton **effacer l’image** , efface l’image actuelle en affectant à sa propriété **image** la **valeur null** (ou, **Nothing**). Chaque événement dans le code inclut des commentaires qui expliquent la fonction du code.

> [!TIP]
> En guise de bonne pratique, veillez à toujours commenter votre code. Les commentaires sont des informations qu'une personne peut lire, et il est toujours utile de prendre un peu de temps pour détailler les objectifs de votre code. Tout le contenu d'une ligne de commentaire est ignoré par le programme. Dans C#, vous commentez une ligne en tapant deux barres obliques au début (//), et dans Visual Basic vous commentez une ligne en commençant par un guillemet simple (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Comment écrire du code pour des boutons supplémentaires et une case à cocher

Ajoutez le code suivant à votre fichier de code **Form1** (*Form1.cs* ou *Form1.vb*).
> [!IMPORTANT]
> Utilisez le contrôle de langage de programmation en haut à droite de cette page pour afficher C# l’extrait de code ou le Visual Basic extrait de code.<br><br>![Contrôle du langage de programmation pour Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

## <a name="next-steps"></a>Étapes suivantes

* Pour passer à l’étape suivante du tutoriel, consultez [Étape 11 : Exécuter votre programme et tester d’autres fonctionnalités](../ide/step-11-run-your-program-and-try-other-features.md).

* Pour revenir à l’étape précédente du tutoriel, consultez [Étape 9 : Passer en revue, commenter et tester votre code](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Voir aussi

* [Tutoriel 2 : Créer un questionnaire mathématique chronométré](tutorial-2-create-a-timed-math-quiz.md)
* [Tutoriel 3 : Créer un jeu de combinaisons](tutorial-3-create-a-matching-game.md)
