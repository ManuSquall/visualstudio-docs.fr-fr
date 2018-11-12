---
title: 'Étape 8 : personnaliser le questionnaire'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09d020e2d83e7e631fefcb1503eb8f1938894986
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672117"
---
# <a name="step-8-customize-the-quiz"></a>Étape 8 : personnaliser le questionnaire
Dans la dernière partie du didacticiel, vous allez découvrir quelques méthodes permettant de personnaliser le questionnaire et développer ce que vous avez déjà appris. Par exemple, pensez à la façon dont le programme crée des problèmes de division aléatoire pour laquelle la réponse n’est jamais une fraction. Pour en savoir plus, définissez le contrôle `timeLabel` sur une couleur différente et donnez un indice à la personne interrogée.  

## <a name="to-customize-the-quiz"></a>Pour personnaliser le questionnaire  

-   Quand il ne reste plus que cinq secondes dans un questionnaire, mettez le contrôle **timeLabel** en rouge en définissant sa propriété **BackColor** (`timeLabel.BackColor = Color.Red;`). Réinitialisez la couleur une fois le questionnaire terminé.  
  
-   Donnez un indice à la personne interrogée en émettant un son quand une réponse correcte est entrée dans un contrôle <xref:System.Windows.Forms.NumericUpDown>. (Vous devez écrire un gestionnaire d’événements pour chaque événement <xref:System.Windows.Forms.NumericUpDown.ValueChanged> du contrôle, qui se déclenche chaque fois que la personne interrogée modifie la valeur du contrôle.)  
  
## <a name="to-continue-or-review"></a>Pour continuer ou examiner  
  
-   Pour télécharger la version finale du questionnaire, consultez [Exemple complet de questionnaire de mathématiques du tutoriel](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Pour passer à l’étape suivante du tutoriel, consultez [Tutoriel 3 : créer un jeu de combinaisons](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Pour revenir à l’étape précédente du tutoriel, consultez [Étape 7 : ajouter des problèmes de multiplication et de division](../ide/step-7-add-multiplication-and-division-problems.md).
