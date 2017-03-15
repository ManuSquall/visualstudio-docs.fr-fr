---
title: "L’attribut &#39;&lt;nom_attribut&gt;&#39; ne peut pas &#234;tre appliqu&#233; &#224; une m&#233;thode avec des param&#232;tres optionnels | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30645"
  - "bc30645"
helpviewer_keywords: 
  - "BC30645"
ms.assetid: 4de3d2c9-5588-47c2-a6b2-e165d16106b8
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’attribut &#39;&lt;nom_attribut&gt;&#39; ne peut pas &#234;tre appliqu&#233; &#224; une m&#233;thode avec des param&#232;tres optionnels
L’attribut peut uniquement être utilisé avec des méthodes qui utilisent des arguments obligatoires ou des méthodes qui n’utilisent aucun argument.  
  
 **ID d’erreur :** BC30645  
  
### Pour corriger cette erreur  
  
1.  Définissez la méthode sans paramètres facultatifs.  
  
2.  Utilisez un attribut qui peut être utilisé avec des méthodes ayant des paramètres facultatifs.  
  
3.  Définissez un attribut personnalisé qui peut être utilisé dans ce contexte.  
  
## Voir aussi  
 <xref:System.AttributeUsageAttribute>   
 [NOT IN BUILD : Attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)