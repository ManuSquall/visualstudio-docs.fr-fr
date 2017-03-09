---
title: "D&#233;pannage des exceptions&#160;: System.MissingFieldException | Microsoft Docs"
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
  - "MissingFieldException (classe)"
ms.assetid: afa4d669-7d08-4b14-8341-36717a5054d6
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.MissingFieldException
Une exception <xref:System.MissingFieldException> est levée lors d'une tentative d'accès dynamique à un champ qui n'existe pas.  
  
## Conseils associés  
 **Si un champ dans une bibliothèque de classes a été supprimé ou renommé, recompilez tous les assemblys qui font référence à la bibliothèque.**  
 Cette exception est générée lors d'une tentative d'accès dynamique à un champ supprimé ou renommé d'un assembly qui n'est pas référencé sous son nom fort.  
  
## Voir aussi  
 <xref:System.MissingFieldException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)