---
title: "D&#233;pannage des exceptions&#160;: System.MissingMethodException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
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
  - "MissingMethodException (classe)"
ms.assetid: 1ca4c351-ca26-4a6d-a5a1-c484ac193e2e
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.MissingMethodException
Une exception <xref:System.MissingMethodException> est levée lors d'une tentative d'accès dynamique à une méthode qui n'existe pas.  
  
## Conseils associés  
 **Si une méthode dans une bibliothèque de classes a été supprimée ou renommée, recompilez tous les assemblys qui y font référence.**  
 Cette exception est généralement levée lors d'une tentative d'accès dynamique à une méthode supprimée ou renommée d'un assembly qui n'est pas référencé sous son nom fort.  
  
## Notes  
 Si vous appelez une fonction non managée, cette exception est levée si le CLR ne peut pas trouver le module ou la fonction.  
  
## Voir aussi  
 <xref:System.MissingMethodException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Troubleshooting Interoperability](/dotnet/visual-basic/programming-guide/com-interop/troubleshooting-interoperability)