---
title: "D&#233;pannage des exceptions&#160;: System.Net.Sockets.SocketException | Microsoft Docs"
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
  - "SocketException (classe)"
ms.assetid: 89e8194d-83b0-450f-91f5-548e5c13944d
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Net.Sockets.SocketException
Une exception <xref:System.Net.Sockets.SocketException> est levée par les classes <xref:System.Net.Sockets.Socket> et <xref:System.Net.Dns> lorsqu'une erreur se produit sur le réseau.  
  
## Conseils associés  
 **Vérifiez la propriété ErrorCode pour déterminer l'origine de l'erreur de socket.**  
 Le constructeur par défaut de la classe <xref:System.Net.Sockets.SocketException> définit la propriété <xref:System.Net.Sockets.SocketException.ErrorCode%2A> sur la dernière erreur de socket survenue sur le système d'exploitation.  
  
## Voir aussi  
 <xref:System.Net.Sockets.SocketException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Utilisation du protocole Secure Sockets Layer](../Topic/Using%20Secure%20Sockets%20Layer.md)