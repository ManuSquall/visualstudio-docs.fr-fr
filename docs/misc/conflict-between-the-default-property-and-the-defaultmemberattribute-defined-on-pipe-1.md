---
title: "Conflit entre la propri&#233;t&#233; par d&#233;faut et le &#39;DefaultMemberAttribute&#39; d&#233;fini pour &#39;|1&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32304"
  - "bc32304"
helpviewer_keywords: 
  - "BC32304"
ms.assetid: 42803d13-ff1d-40ed-a4a8-269e2fb4aa01
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Conflit entre la propri&#233;t&#233; par d&#233;faut et le &#39;DefaultMemberAttribute&#39; d&#233;fini pour &#39;|1&#39;
Une classe, une structure ou une interface déclare une propriété par défaut avec le mot clé [Default](/dotnet/visual-basic/language-reference/modifiers/default), mais elle applique aussi le <xref:System.Reflection.DefaultMemberAttribute> pour désigner un autre membre comme membre par défaut.  
  
 Un type peut avoir au plus un membre par défaut. Lorsque vous déclarez une propriété par défaut, Visual Basic applique automatiquement le <xref:System.Reflection.DefaultMemberAttribute> à la classe, structure ou interface qui désigne cette propriété.  
  
 **ID d’erreur :** BC32304  
  
### Pour corriger cette erreur  
  
1.  Déterminez quel membre doit être le membre par défaut de la classe, structure ou interface.  
  
2.  Supprimez la déclaration conflictuelle \(le mot clé `Default` ou le <xref:System.Reflection.DefaultMemberAttribute>\).  
  
## Voir aussi  
 <xref:System.Reflection.DefaultMemberAttribute>   
 [Default](/dotnet/visual-basic/language-reference/modifiers/default)   
 [NOT IN BUILD : Propriétés par défaut](http://msdn.microsoft.com/fr-fr/a70f2a27-8176-4858-935e-f25afdd43ab5)   
 [How to: Declare and Call a Default Property in Visual Basic](../Topic/How%20to:%20Declare%20and%20Call%20a%20Default%20Property%20in%20Visual%20Basic.md)