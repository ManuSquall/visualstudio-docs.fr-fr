---
title: 'Étape 8 : personnaliser le questionnaire'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cee7b855256f352c9ac9ed39994191f4a9e6d946
ms.sourcegitcommit: 98b02f87c7aa1f5eb7f0d1c86bfa36efa8580c57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314209"
---
# <a name="step-8-customize-the-quiz"></a>Étape 8 : personnaliser le questionnaire

Dans la dernière partie du didacticiel, vous allez découvrir quelques méthodes permettant de personnaliser le questionnaire et développer ce que vous avez déjà appris. Par exemple, pensez à la façon dont le programme crée des problèmes de division aléatoire pour laquelle la réponse n’est jamais une fraction. Pour en savoir plus, définissez le contrôle `timeLabel` sur une couleur différente et donnez un indice à la personne interrogée.

> [!NOTE]
> Cette rubrique fait partie d'une série de didacticiels sur les concepts de codage de base.
> - Pour obtenir une vue d’ensemble du tutoriel, consultez [Tutoriel 2 : créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Pour télécharger une version complète du code, consultez l' [exemple complet de didacticiels mathématiques](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-customize-the-quiz"></a>Pour personnaliser le questionnaire

- Lorsque seulement cinq secondes sont conservées dans un quiz, désactivez le contrôle **timeLabel** en définissant sa propriété **BackColor** .

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  Réinitialisez la couleur une fois le questionnaire terminé.

- Donnez un indice à la personne interrogée en émettant un son quand une réponse correcte est entrée dans un contrôle <xref:System.Windows.Forms.NumericUpDown>. (Vous devez écrire un gestionnaire d’événements pour chaque événement <xref:System.Windows.Forms.NumericUpDown.ValueChanged> du contrôle, qui se déclenche chaque fois que la personne interrogée modifie la valeur du contrôle.)

## <a name="to-continue-or-review"></a>Pour continuer ou examiner

- Pour passer au didacticiel suivant, consultez **[didacticiel 3 : créer un jeu de combinaisons](../ide/tutorial-3-create-a-matching-game.md)** .

- Pour revenir à l’étape précédente du tutoriel, consultez [Étape 7 : ajouter des problèmes de multiplication et de division](../ide/step-7-add-multiplication-and-division-problems.md).
