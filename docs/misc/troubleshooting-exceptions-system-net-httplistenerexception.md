---
title: "D&#233;pannage des exceptions&#160;: System.Net.HttpListenerException | Microsoft Docs"
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
  - "HttpListenerException (classe)"
ms.assetid: 1595c5b6-4710-4076-9bfc-9f70f52e679a
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Net.HttpListenerException
Une <xref:System.Net.HttpListenerException> est levée lorsqu'une erreur se produit lors du traitement d'une demande HTTP \(Hypertext Transfer Protocol\).  
  
## Conseils associés  
 Assurez\-vous que vous n'essayez pas d''inscrire un préfixe URI qui l'est déjà.  
 Si le préfixe URI est déjà inscrit, cette exception se produira.  
  
 Assurez\-vous que votre requête HTTP est valide.  
 Cette exception est levée par la classe <xref:System.Net.HttpListener> et ses classes associées lorsqu'une erreur se produit pendant l'initialisation du <xref:System.Net.HttpListener> ou en créant ou envoyant une réponse à une requête HTTP.  
  
 Si vous utilisez la méthode `HttpListenerPrefixCollection.Add`, assurez\-vous que `uriPrefix` n'a pas déjà été ajouté.  
 Cette exception sera levée si un autre <xref:System.Net.HttpListener> a déjà ajouté le préfixe `uriPrefix`.  
  
## Voir aussi  
 <xref:System.Net.HttpListenerException>   
 <xref:System.Net.HttpListener>   
 <xref:System.Net.HttpListenerPrefixCollection>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)