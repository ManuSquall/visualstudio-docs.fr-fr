---
title: "D&#233;pannage des exceptions&#160;: System.FieldAccessException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "FieldAccessException (classe)"
ms.assetid: 47a72daf-500e-494c-b2fe-374edad2e9cd
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.FieldAccessException
Une exception <xref:System.FieldAccessException> est levée lors d'une tentative non valide d'accès à un champ privé ou protégé à l'intérieur d'une classe.  
  
## Conseils associés  
 **Si le niveau d'accès d'un champ dans une bibliothèque de classes a changé, recompilez tous les assemblys qui font référence à cette bibliothèque.**  
 Cette exception est généralement levée lorsque le niveau d'accès \(`Public`, `Private`, etc.\) d'un champ figurant dans une bibliothèque de classes a été modifié et qu'un ou plusieurs assemblys référençant cette bibliothèque n'ont pas été recompilés.  
  
## Voir aussi  
 <xref:System.FieldAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)