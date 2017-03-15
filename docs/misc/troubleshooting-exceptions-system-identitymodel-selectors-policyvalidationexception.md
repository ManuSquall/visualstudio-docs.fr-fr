---
title: "D&#233;pannage des exceptions&#160;: System.IdentityModel.Selectors.PolicyValidationException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PolicyValidationException (exception)"
  - "System.IdentityModel.Selectors.PolicyValidationException (exception)"
ms.assetid: 510c7698-a12b-4bcb-a9d8-87c704b62ffa
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.IdentityModel.Selectors.PolicyValidationException
Une exception <xref:System.IdentityModel.Selectors.PolicyValidationException> est levée lorsque la stratégie fournie par le destinataire ne peut pas être validée. Pour plus d’informations sur les spécifications de stratégie, consultez [A Technical Reference for the Information Card Profile V1.0](http://go.microsoft.com/fwlink/?LinkID=102401).  
  
 Tout contenu de stratégie non valide peut provoquer cette défaillance. Les problèmes courants avec le contenu de stratégie sont les suivants :  
  
-   Type de clé non valide  
  
-   Taille de clé non valide  
  
-   XML non valide  
  
-   Aucune revendication spécifiée dans la stratégie \(au moins une revendication non facultative doit être spécifiée\)  
  
## Voir aussi  
 <xref:System.IdentityModel.Selectors.PolicyValidationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)