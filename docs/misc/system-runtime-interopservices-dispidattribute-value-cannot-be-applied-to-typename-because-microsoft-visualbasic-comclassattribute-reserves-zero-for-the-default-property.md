---
title: "Impossible d’appliquer &#39;System.Runtime.InteropServices.DispIdAttribute&#39; &#224; &#39;&lt;nom_type&gt;&#39;, car &#39;Microsoft.VisualBasic.ComClassAttribute&#39; r&#233;serve z&#233;ro &#224; la propri&#233;t&#233; par d&#233;faut | Microsoft Docs"
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
  - "vbc32505"
  - "bc32505"
helpviewer_keywords: 
  - "BC32505"
ms.assetid: a7d5b948-2d72-48b1-8baf-bfaae36b0128
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’appliquer &#39;System.Runtime.InteropServices.DispIdAttribute&#39; &#224; &#39;&lt;nom_type&gt;&#39;, car &#39;Microsoft.VisualBasic.ComClassAttribute&#39; r&#233;serve z&#233;ro &#224; la propri&#233;t&#233; par d&#233;faut
Un bloc d’attributs <xref:System.Runtime.InteropServices.DispIdAttribute> spécifie une valeur DISPID égale à 0, qui est réservée par `COMClassAttribute` pour représenter la propriété par défaut de la classe à laquelle elle est appliquée.  
  
 L’identificateur de dispatch \(DISPID\) est utilisé dans COM en tant qu’argument de la méthode `IDispatch:Invoke` pour accéder aux propriétés et aux méthodes exposées par un objet COM.  
  
 **ID d’erreur :** BC32505  
  
### Pour corriger cette erreur  
  
-   Spécifiez une valeur DISPID supérieure à zéro dans <xref:System.Runtime.InteropServices.DispIdAttribute>.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.DispIdAttribute>   
 [NOT IN BUILD : Attributs utilisés en Visual Basic](http://msdn.microsoft.com/fr-fr/22231318-8a40-49af-9245-e0aab723563b)   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute, classe](http://msdn.microsoft.com/fr-fr/5c2f0835-9210-47dc-bc59-5c1769953574)