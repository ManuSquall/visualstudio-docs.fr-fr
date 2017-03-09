---
title: "L’attribut &#39;&lt;nom_attribut&gt;&#39; ne peut pas &#234;tre sp&#233;cifi&#233; plusieurs fois dans ce projet, m&#234;me avec des valeurs de param&#232;tre identiques | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc41000"
  - "vbc41000"
helpviewer_keywords: 
  - "BC41000"
ms.assetid: 7e846177-7b89-44da-8f17-cdc8606ef148
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’attribut &#39;&lt;nom_attribut&gt;&#39; ne peut pas &#234;tre sp&#233;cifi&#233; plusieurs fois dans ce projet, m&#234;me avec des valeurs de param&#232;tre identiques
Un attribut personnalisé est spécifié plusieurs fois sur le même élément de programmation, mais un <xref:System.AttributeUsageAttribute> est appliqué à l’attribut personnalisé et sa propriété <xref:System.AttributeUsageAttribute.AllowMultiple%2A> est définie sur `False`.<xref:System.AttributeUsageAttribute.AllowMultiple%2A> permet de contrôler si l’attribut peut être à usages multiples.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC41000  
  
### Pour corriger cette erreur  
  
-   Supprimez la spécification supplémentaire de l’attribut personnalisé, ou définissez <xref:System.AttributeUsageAttribute.AllowMultiple%2A> sur `True` dans le <xref:System.AttributeUsageAttribute> auquel il est appliqué.  
  
## Voir aussi  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A>   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)