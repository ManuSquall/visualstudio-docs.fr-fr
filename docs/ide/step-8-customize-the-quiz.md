---
title: 'Étape 8 : Personnaliser le questionnaire'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 86fb0b7d22e02e563fe022b470651e2c335e4000
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079455"
---
# <a name="step-8-customize-the-quiz"></a>Étape 8 : Personnaliser le questionnaire

Dans la dernière partie du didacticiel, vous allez découvrir quelques méthodes permettant de personnaliser le questionnaire et développer ce que vous avez déjà appris. Par exemple, pensez à la façon dont le programme crée des problèmes de division aléatoire pour laquelle la réponse n’est jamais une fraction. Pour en savoir plus, définissez le contrôle `timeLabel` sur une couleur différente et donnez un indice à la personne interrogée.

> [!NOTE]
> Cette rubrique fait partie d'une série de didacticiels sur les concepts de codage de base.
> - Pour obtenir une vue d’ensemble du tutoriel, consultez [Tutoriel 2 : Créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Pour télécharger une version complète du code, consultez l' [exemple complet de didacticiels mathématiques](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-customize-the-quiz"></a>Pour personnaliser le questionnaire

- Lorsque seulement cinq secondes sont conservées dans un quiz, désactivez le contrôle **timeLabel** en définissant sa propriété **BackColor** .

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  > [!IMPORTANT]
  > Utilisez le contrôle de langage de programmation en haut à droite de cette page pour afficher C# l’extrait de code ou le Visual Basic extrait de code.<br><br>![Contrôle du langage de programmation pour Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

  Réinitialisez la couleur une fois le questionnaire terminé.

- Donnez un indice à la personne interrogée en émettant un son quand une réponse correcte est entrée dans un contrôle <xref:System.Windows.Forms.NumericUpDown>. (Vous devez écrire un gestionnaire d’événements pour chaque événement <xref:System.Windows.Forms.NumericUpDown.ValueChanged> du contrôle, qui se déclenche chaque fois que la personne interrogée modifie la valeur du contrôle.)

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer au didacticiel suivant, consultez  **[didacticiel 3 : Créer un jeu](../ide/tutorial-3-create-a-matching-game.md)** de combinaisons.

- Pour revenir à l’étape précédente du tutoriel, consultez [Étape 7 : Ajouter des problèmes de multiplication et de division](../ide/step-7-add-multiplication-and-division-problems.md).
