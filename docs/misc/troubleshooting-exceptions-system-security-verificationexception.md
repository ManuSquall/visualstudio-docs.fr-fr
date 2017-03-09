---
title: "D&#233;pannage des exceptions&#160;: System.Security.VerificationException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHVerification"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "VerificationException (classe)"
ms.assetid: b7b1a4c2-6769-46bd-8912-ebbfe226bfb3
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Security.VerificationException
Une exception <xref:System.Security.VerificationException> est levée lorsque la stratégie de sécurité nécessite que du code soit de type sécurisé et que le processus de vérification est incapable de vérifier que le code est de type sécurisé.  
  
## Conseils associés  
 Assurez\-vous que votre application ne charge pas deux versions conflictuelles d'une bibliothèque de classes.  
 Dans le cadre du processus de vérification, le type de sécurité de MSIL \(Microsoft Intermediate Language\) est vérifié pour s'assurer que les objets sont isolés les uns des autres de manière sécurisée et qu'ils sont donc à l'abri de toute altération accidentelle ou malveillante. Pour plus d’informations, consultez [Sécurité de type et sécurité](http://msdn.microsoft.com/fr-fr/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc).  
  
## Voir aussi  
 <xref:System.Security.VerificationException>   
 <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)