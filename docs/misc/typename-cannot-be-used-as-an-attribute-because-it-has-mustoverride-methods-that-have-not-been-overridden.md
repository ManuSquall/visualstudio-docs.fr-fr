---
title: "&#39;&lt;nom_type&gt;&#39; ne peut pas &#234;tre utilis&#233; en tant qu’attribut, car il comporte des m&#233;thodes &#39;MustOverride&#39; qui n’ont pas &#233;t&#233; substitu&#233;es | Microsoft Docs"
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
  - "bc31507"
  - "vbc31507"
helpviewer_keywords: 
  - "BC31507"
ms.assetid: 843643d3-3e81-4ce3-b4df-278882f3954d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_type&gt;&#39; ne peut pas &#234;tre utilis&#233; en tant qu’attribut, car il comporte des m&#233;thodes &#39;MustOverride&#39; qui n’ont pas &#233;t&#233; substitu&#233;es
Les classes avec des méthodes `MustOverride` ne peuvent pas être utilisées en tant qu’attributs.  
  
 Vous ne pouvez utiliser les membres `MustOverride` des classes d’attributs qu’à partir de classes dérivées qui se substituent à des membres de ce type.  
  
 **ID d’erreur :** BC31507  
  
### Pour corriger cette erreur  
  
1.  Supprimez le modificateur `MustOverride` des membres de classes d’attributs.  
  
2.  Implémentez les membres `MustOverride` dans une classe dérivée et utilisez cette classe en tant qu’attribut.  
  
## Voir aussi  
 <xref:System.AttributeUsageAttribute>   
 [NOT IN BUILD : Attributs personnalisés en Visual Basic](http://msdn.microsoft.com/fr-fr/d72d8a5c-8f64-4614-b15b-cad66845d047)