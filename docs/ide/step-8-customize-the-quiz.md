---
title: "Étape 8 : personnaliser le questionnaire | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: "12"
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 7a4481f9a13d6807abc42b938670a05bd0dda50b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="step-8-customize-the-quiz"></a>Étape 8 : personnaliser le questionnaire
Dans la dernière partie du didacticiel, vous allez découvrir quelques méthodes permettant de personnaliser le questionnaire et développer ce que vous avez déjà appris. Par exemple, pensez à la façon dont le programme crée des problèmes de division aléatoire pour laquelle la réponse n’est jamais une fraction. Pour en savoir plus, définissez le contrôle `timeLabel` sur une couleur différente et donnez un indice à la personne interrogée.  
  
### <a name="to-customize-the-quiz"></a>Pour personnaliser le questionnaire  
  
-   Quand il ne reste plus que cinq secondes dans un questionnaire, mettez le contrôle **timeLabel** en rouge en définissant sa propriété **BackColor** (`timeLabel.BackColor = Color.Red;`). Réinitialisez la couleur une fois le questionnaire terminé.  
  
-   Donnez un indice à la personne interrogée en émettant un son quand une réponse correcte est entrée dans un contrôle NumericUpDown. (Vous devez écrire un gestionnaire d’événements pour chaque événement `ValueChanged()` du contrôle, qui se déclenche chaque fois que la personne interrogée modifie la valeur du contrôle.)  
  
### <a name="to-continue-or-review"></a>Pour continuer ou examiner  
  
-   Pour télécharger la version finale du questionnaire, consultez [Exemple complet de questionnaire de mathématiques du didacticiel](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Pour passer à l’étape suivante du didacticiel, consultez [Didacticiel 3 : créer un jeu de combinaisons](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Pour revenir à l’étape précédente du didacticiel, consultez [Étape 7 : ajouter des problèmes de multiplication et de division](../ide/step-7-add-multiplication-and-division-problems.md).