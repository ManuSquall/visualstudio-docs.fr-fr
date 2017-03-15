---
title: "&#39;&lt;nom_attribut&gt;&#39; ne peut pas &#234;tre appliqu&#233; plusieurs fois &#224; un assembly | Microsoft Docs"
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
  - "bc31521"
  - "vbc31521"
helpviewer_keywords: 
  - "BC31521"
ms.assetid: 7312570f-8afb-4afe-992f-b6f7796f5f26
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_attribut&gt;&#39; ne peut pas &#234;tre appliqu&#233; plusieurs fois &#224; un assembly
L’attribut spécifié ne peut être appliqué qu’une seule fois à un attribut.  
  
 **ID d’erreur :** BC31521  
  
### Pour corriger cette erreur  
  
1.  Supprimez les applications redondantes de cet attribut.  
  
2.  Si vous utilisez un attribut personnalisé que vous avez développé, modifiez `AttributeUsageAttribute` puis définissez la propriété `AllowMultiple` sur `True`.  
  
## Voir aussi  
 <xref:System.AttributeUsageAttribute>   
 <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=fullName>