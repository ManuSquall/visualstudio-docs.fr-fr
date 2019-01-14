---
title: 'Étape 8 : Personnaliser le questionnaire'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2b2f9d46b623f63d216ce530cd283bf799a3a73
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842354"
---
# <a name="step-8-customize-the-quiz"></a>Étape 8 : Personnaliser le questionnaire
Dans la dernière partie du didacticiel, vous allez découvrir quelques méthodes permettant de personnaliser le questionnaire et développer ce que vous avez déjà appris. Par exemple, pensez à la façon dont le programme crée des problèmes de division aléatoire pour laquelle la réponse n’est jamais une fraction. Pour en savoir plus, définissez le contrôle `timeLabel` sur une couleur différente et donnez un indice à la personne interrogée.  

## <a name="to-customize-the-quiz"></a>Pour personnaliser le questionnaire  

-   Quand il ne reste plus que cinq secondes dans un questionnaire, mettez le contrôle **timeLabel** en rouge en définissant sa propriété **BackColor** (`timeLabel.BackColor = Color.Red;`). Réinitialisez la couleur une fois le questionnaire terminé.  
  
-   Donnez un indice à la personne interrogée en émettant un son quand une réponse correcte est entrée dans un contrôle <xref:System.Windows.Forms.NumericUpDown>. (Vous devez écrire un gestionnaire d’événements pour chaque événement <xref:System.Windows.Forms.NumericUpDown.ValueChanged> du contrôle, qui se déclenche chaque fois que la personne interrogée modifie la valeur du contrôle.)  
  
## <a name="to-continue-or-review"></a>Pour continuer ou examiner  
  
-   Pour télécharger la version finale du questionnaire, consultez [Exemple complet de questionnaire de mathématiques du tutoriel](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Pour passer à l’étape suivante du tutoriel, consultez [Tutoriel 3 : Créer un jeu de combinaisons](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Pour revenir à l’étape précédente du tutoriel, consultez [Étape 7 : Ajouter des problèmes de multiplication et de division](../ide/step-7-add-multiplication-and-division-problems.md).
