---
title: "D&#233;pannage des exceptions&#160;: System.Net.WebException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "WebException (classe)"
ms.assetid: 6cd69a2c-c52b-420d-be47-a4e34eaec6f3
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Net.WebException
Une exception <xref:System.Net.WebException> est levée en cas d'erreur lors de l'accès au réseau via un protocole enfichable.  
  
## Conseils associés  
 **Vérifiez la propriété Response de l'exception pour déterminer la raison de l'échec de la demande.**  
 Lorsqu'une exception <xref:System.Net.WebException> est levée par un descendant de la classe <xref:System.Net.WebRequest>, la propriété <xref:System.Net.WebException.Response%2A> fournit la réponse Internet à l'application.  
  
 **Vérifiez la propriété Status de l'exception pour déterminer la raison de l'échec de la demande.**  
 La propriété <xref:System.Net.WebException.Status%2A> de l'exception fournit des informations sur l'état de l'erreur. Pour plus d'informations, consultez <xref:System.Net.WebExceptionStatus>.  
  
 **Si votre appel expire lorsque vous exécutez pas à pas un service Web XML, définissez une valeur infinie pour le délai d'attente de l'appel du service Web XML.**  
 Pour plus d'informations, consultez [Erreur : délai d'attente lors du débogage de services Web](../debugger/error-timeout-while-debugging-web-services.md).  
  
## Voir aussi  
 <xref:System.Net.WebException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Comment : envoyer des données à l’aide de la classe WebRequest](../Topic/How%20to:%20Send%20Data%20Using%20the%20WebRequest%20Class.md)   
 [Procédure : demande de données à l’aide de la classe WebRequest](../Topic/How%20to:%20Request%20Data%20Using%20the%20WebRequest%20Class.md)   
 [Comment : récupérer une classe WebResponse spécifique au protocole qui correspond à une classe WebRequest](../Topic/How%20to:%20Retrieve%20a%20Protocol-Specific%20WebResponse%20that%20Matches%20a%20WebRequest.md)