---
title: "Les tableaux de type &#39;System.Void&#39; ne sont pas autoris&#233;s dans cette expression | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31428"
  - "bc31428"
helpviewer_keywords: 
  - "BC31428"
ms.assetid: 21d77b56-585f-4107-b7ec-21933ba58017
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les tableaux de type &#39;System.Void&#39; ne sont pas autoris&#233;s dans cette expression
Une expression dans une instruction d’assignation ou une déclaration spécifie un tableau de type <xref:System.Void>.  
  
 La structure <xref:System.Void> est un type spécialisé utilisé en interne par le .NET Framework et en particulier par Visual C\# et Visual C\+\+. Elle représente un type valeur de retour pour une méthode qui ne retourne pas de valeur. Visual Basic utilise une procédure `Sub` quand aucune valeur n’est retournée et une procédure `Function` quand une valeur est retournée.  
  
 Les tableaux de type <xref:System.Void> ne sont pas explicites et ne sont pas autorisés dans n’importe quel contexte.  
  
 **ID d’erreur :** BC31428  
  
### Pour corriger cette erreur  
  
1.  Supprimez les parenthèses qui désignent un tableau.  
  
2.  À moins que vous n’ayez une raison particulière de comparer un type d’exécution à <xref:System.Void>, supprimez entièrement la référence à ce type.  
  
## Voir aussi  
 <xref:System.Void>