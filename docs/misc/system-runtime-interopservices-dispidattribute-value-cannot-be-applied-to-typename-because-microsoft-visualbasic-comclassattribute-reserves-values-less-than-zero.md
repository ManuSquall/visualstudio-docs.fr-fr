---
title: "Impossible d’appliquer la valeur &#39;System.Runtime.InteropServices.DispIdAttribute&#39; &#224; &#39;&lt;nom_type&gt;&#39;, car &#39;Microsoft.VisualBasic.ComClassAttribute&#39; r&#233;serve les valeurs inf&#233;rieures &#224; z&#233;ro | Microsoft Docs"
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
  - "bc32506"
  - "vbc32506"
helpviewer_keywords: 
  - "BC32506"
ms.assetid: c6f52e1d-45d8-45cb-9ecb-a2f23b3ca779
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible d’appliquer la valeur &#39;System.Runtime.InteropServices.DispIdAttribute&#39; &#224; &#39;&lt;nom_type&gt;&#39;, car &#39;Microsoft.VisualBasic.ComClassAttribute&#39; r&#233;serve les valeurs inf&#233;rieures &#224; z&#233;ro
Un bloc d’attributs <xref:System.Runtime.InteropServices.DispIdAttribute> spécifie une valeur DISPID inférieure à 0, ce qui est réservé par `COMClassAttribute` pour les fonctions spéciales sur la classe à laquelle il est appliqué.  
  
 L’identificateur de dispatch \(DISPID\) est utilisé dans COM en tant qu’argument de la méthode `IDispatch:Invoke` pour accéder aux propriétés et méthodes exposées par un objet COM.  
  
 **ID d’erreur :** BC32506  
  
### Pour corriger cette erreur  
  
-   Spécifiez une valeur DISPID supérieure à zéro dans `DispIdAttribute`.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.DispIdAttribute>   
 [NOT IN BUILD : Attributs utilisés en Visual Basic](http://msdn.microsoft.com/fr-fr/22231318-8a40-49af-9245-e0aab723563b)   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [ComClassAttribute, classe](http://msdn.microsoft.com/fr-fr/5c2f0835-9210-47dc-bc59-5c1769953574)