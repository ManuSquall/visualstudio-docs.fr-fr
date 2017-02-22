---
title: "&#201;tape&#160;8&#160;: Personnaliser le questionnaire | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# &#201;tape&#160;8&#160;: Personnaliser le questionnaire
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans la dernière partie du didacticiel, vous explorerez quelques façons de personnaliser le questionnaire et de développer ce que vous avez déjà découvert.  Par exemple, réfléchissez à la façon dont le programme crée les problèmes aléatoire de division pour lesquels la réponse n'est jamais une fraction.  Pour découvrir d'autres fonctionnalités, changez la couleur du contrôle `timeLabel` et proposez une aide à l'utilisateur.  
  
### Pour personnaliser le quizz  
  
-   Lorsqu'il ne reste plus que cinq secondes dans un questionnaire, mettez le contrôle **timeLabel** en rouge en définissant sa propriété **CouleurFond** \(`timeLabel.BackColor = Color.Red;`\).  Réinitialisez la couleur lorsque le questionnaire est terminé.  
  
-   Fournissez une aide à l'utilisateur en lisant un son lorsqu'une réponse correcte est entrée dans un contrôles NumericUpDown. \(Vous devez écrire un gestionnaire d'événements pour l'événement  `ValueChanged()` de chaque contrôle, qui se déclenche chaque fois que l'utilisateur modifie la valeur du contrôle.\)  
  
### Pour continuer ou examiner  
  
-   Pour télécharger une version complète du questionnaire, voir [Exécutez l'exemple d'instruction du questionnaire de mathématiques](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
-   Pour passer à l'étape suivante du didacticiel, consultez [Didacticiel 3 : créer un jeu de combinaisons](../ide/tutorial-3-create-a-matching-game.md).  
  
-   Pour revenir à l'étape précédente du didacticiel, consultez [Étape 7 : ajouter des problèmes de multiplication et de division](../Topic/Step%207:%20Add%20Multiplication%20and%20Division%20Problems.md).