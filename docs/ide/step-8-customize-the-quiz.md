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
ms.openlocfilehash: 32c35c0eccc4c6a4972774219dc07b606b72243c
ms.sourcegitcommit: 10d16e18c5f5e482c4c2856e6cacaad283463b65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75776021"
---
# <a name="step-8-customize-the-quiz"></a>Étape 8 : personnaliser le questionnaire

Dans la dernière partie du didacticiel, vous allez découvrir quelques méthodes permettant de personnaliser le questionnaire et développer ce que vous avez déjà appris. Par exemple, pensez à la façon dont le programme crée des problèmes de division aléatoire pour laquelle la réponse n’est jamais une fraction. Pour en savoir plus, définissez le contrôle `timeLabel` sur une couleur différente et donnez un indice à la personne interrogée.

> [!NOTE]
> Cette rubrique fait partie d'une série de didacticiels sur les concepts de codage de base. Pour obtenir une vue d’ensemble du tutoriel, consultez [Tutoriel 2 : créer un questionnaire mathématique chronométré](../ide/tutorial-2-create-a-timed-math-quiz.md).

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
