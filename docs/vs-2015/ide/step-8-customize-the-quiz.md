---
title: 'Étape 8 : personnaliser le questionnaire | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 559bd2a1b908ab5b1590a2ec2dd71225020db79a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260141"
---
# <a name="step-8-customize-the-quiz"></a>Étape 8 : personnaliser le questionnaire
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans la dernière partie du didacticiel, vous allez découvrir quelques méthodes permettant de personnaliser le questionnaire et développer ce que vous avez déjà appris. Par exemple, pensez à la façon dont le programme crée des problèmes de division aléatoire pour laquelle la réponse n’est jamais une fraction. Pour en savoir plus, définissez le contrôle `timeLabel` sur une couleur différente et donnez un indice à la personne interrogée.  
  
### <a name="to-customize-the-quiz"></a>Pour personnaliser le questionnaire  
  
-   Quand il ne reste plus que cinq secondes dans un questionnaire, mettez le contrôle **timeLabel** en rouge en définissant sa propriété **BackColor** (`timeLabel.BackColor = Color.Red;`). Réinitialisez la couleur une fois le questionnaire terminé.  
  
-   Donnez un indice à la personne interrogée en émettant un son quand une réponse correcte est entrée dans un contrôle NumericUpDown. (Vous devez écrire un gestionnaire d’événements pour chaque événement `ValueChanged()` du contrôle, qui se déclenche chaque fois que la personne interrogée modifie la valeur du contrôle.)  
  
### <a name="to-continue-or-review"></a>Pour continuer ou examiner  
  
-   Pour télécharger la version finale du questionnaire, consultez [Exemple complet de questionnaire de mathématiques du didacticiel](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Pour passer à l’étape suivante du didacticiel, consultez [Didacticiel 3 : créer un jeu de combinaisons](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Pour revenir à l’étape précédente du didacticiel, consultez [Étape 7 : ajouter des problèmes de multiplication et de division](../ide/step-7-add-multiplication-and-division-problems.md).



