---
title: "D&#233;pannage des exceptions&#160;: System.Net.CookieException | Microsoft Docs"
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
  - "CookieException (classe)"
ms.assetid: 7db6b962-cc5e-4b63-be65-894a8f186b38
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# D&#233;pannage des exceptions&#160;: System.Net.CookieException
Une exception <xref:System.Net.CookieException> est levée si une erreur se produit lors de l'ajout d'un cookie à un conteneur de cookie.  
  
## Conseils associés  
 **Assurez\-vous que la taille du cookie n'excède pas la taille maximale autorisée par le conteneur du cookie.**  
 Cette exception est levée lors d'une tentative d'ajout d'un <xref:System.Net.Cookie> dont la longueur dépasse <xref:System.Net.CookieContainer.MaxCookieSize%2A> à un <xref:System.Net.CookieContainer>. La taille de cookie maximale par défaut est 4096 octets.  
  
 **Lors de la définition de la propriété Name d'un cookie, assurez\-vous que la valeur n'est pas une référence null ou une chaîne vide.**  
 La propriété <xref:System.Net.Cookie.Name%2A> doit être initialisée avant d'utiliser une instance de la classe <xref:System.Net.Cookie>. Les caractères suivants sont réservés et ne peuvent pas être utilisés pour cette valeur d'attribut : signe égal, point\-virgule, virgule, retour à la ligne \(\\n\), retour chariot \(\\r\), tabulation \(\\t\). Le signe dollar \($\) ne peut pas être le premier caractère.  
  
 **Lors de la définition de la propriété Port d'un cookie, assurez\-vous que la valeur est valide et encadrée de guillemets doubles.**  
 L'attribut <xref:System.Net.Cookie.Port%2A> restreint les ports auxquels un cookie peut être envoyé. La valeur par défaut signifie aucune restriction. Affecter une chaîne vide \(""\) à la propriété restreint le port à celui utilisé dans la réponse HTTP. Sinon, la valeur doit être une chaîne entre guillemets contenant des valeurs de port séparées par des virgules.  
  
 **Lors de la définition de la propriété Value d'un cookie, assurez\-vous que la valeur n'est pas null.**  
 Les caractères suivants sont réservés et ne peuvent pas être utilisés pour cette propriété : point\-virgule, virgule.  
  
## Voir aussi  
 <xref:System.Net.CookieException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [How to: Write a Cookie](../Topic/How%20to:%20Write%20a%20Cookie.md)