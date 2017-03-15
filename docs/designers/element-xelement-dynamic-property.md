---
title: "Element (propri&#233;t&#233; dynamique XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XElement.Element"
apitype: "Assembly"
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Element (propri&#233;t&#233; dynamique XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtient un indexeur utilisé pour récupérer l'instance d'élément enfant qui correspond au nom développé spécifié.  
  
## Syntaxe  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## Valeur de propriété\/valeur de retour  
 Indexeur de type `XElement Item(String expandedName)`.Cet indexeur prend un paramètre de nom développé et retourne l'objet <xref:System.Xml.Linq.XElement> correspondant ou `null` s'il n'existe aucun élément avec le nom spécifié.  
  
## Notes  
 Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XContainer.Element%2A> de la classe <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Éléments](../designers/elements-xelement-dynamic-property.md)