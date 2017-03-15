---
title: "La m&#233;thode &#39;&lt;nom_m&#233;thode&gt;&#39; dispose d’une demande de liaison, mais se substitue aux m&#233;thodes suivantes qui ne disposent pas de demande de liaison ou les impl&#233;mente. Une faille de s&#233;curit&#233; existe&#160;: | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42200"
  - "vbc42200"
helpviewer_keywords: 
  - "BC42200"
ms.assetid: c79d672e-638c-4d87-9b93-edf12ce84a52
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La m&#233;thode &#39;&lt;nom_m&#233;thode&gt;&#39; dispose d’une demande de liaison, mais se substitue aux m&#233;thodes suivantes qui ne disposent pas de demande de liaison ou les impl&#233;mente. Une faille de s&#233;curit&#233; existe&#160;:
Une action de demande de liaison de sécurité a été ajoutée à la méthode. Cependant, la méthode se substitue aux méthodes ne disposant pas de demande de liaison ou les implémente. Les méthodes substituées ou implémentées peuvent donc être appelées avec des autorisations insuffisantes, ce qui entraîne un problème de sécurité.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC42200  
  
### Pour corriger cette erreur  
  
-   Ajoutez des demandes de liaison aux méthodes substituées et\/ou implémentées.  
  
## Voir aussi  
 [Demandes de liaison](../Topic/Link%20Demands.md)   
 [Demand et LinkDemand](http://msdn.microsoft.com/fr-fr/1ab877f2-70f4-4e0d-8116-943999dfe8f5)   
 [Optimisations de la sécurité](http://msdn.microsoft.com/fr-fr/cf255069-d85d-4de3-914a-e4625215a7c0)