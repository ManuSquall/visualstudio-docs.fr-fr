---
title: "Descendants (propri&#233;t&#233; dynamique XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Descendants (propri&#233;t&#233; dynamique XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtient un indexeur utilisé pour récupérer tous les éléments descendants de l'élément actif qui correspondent au nom développé spécifié.  
  
## Syntaxe  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## Valeur de propriété\/valeur de retour  
 Indexeur de type `IEnumerable<XElement> Item(String expandedName)`.Cet indexeur prend le nom développé des éléments descendants spécifiés et retourne les éléments enfants correspondants dans une collection <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.  
  
## Notes  
 Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> de la classe <xref:System.Xml.Linq.XContainer>.  
  
 Les éléments de la collection retournée sont spécifiés dans l'ordre du document source XML.  
  
 Cette propriété utilise l'exécution différée.  
  
## Voir aussi  
 [Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Éléments](../designers/elements-xelement-dynamic-property.md)