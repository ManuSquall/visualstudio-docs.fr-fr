---
title: "D&#233;pannage des exceptions&#160;: System.MethodAccessException | Microsoft Docs"
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
  - "MethodAccessException (classe)"
ms.assetid: 1c276666-e451-489e-8b95-25d737787030
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.MethodAccessException
Une exception <xref:System.MethodAccessException> est levée lors d'une tentative non valide d'accès à une méthode privée ou protégée à l'intérieur d'une classe.  
  
## Conseils associés  
 **Si le niveau d'accès d'une méthode dans une bibliothèque de classes a changé, recompilez tous les assemblys qui font référence à cette bibliothèque.**  
 Cette exception se produit généralement lorsque l'appelant n'est pas autorisé à accéder au membre.  
  
## Voir aussi  
 <xref:System.MethodAccessException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)