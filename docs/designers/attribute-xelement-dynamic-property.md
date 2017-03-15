---
title: "Attribut (propri&#233;t&#233; dynamique XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Attribut (propri&#233;t&#233; dynamique XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtient un indexeur utilisé pour récupérer l'instance d'attribut qui correspond au nom développé spécifié.  
  
## Syntaxe  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## Valeur de propriété\/valeur de retour  
 Indexeur de type `XAttribute Item(String expandedName)`.Cet indexeur prend le nom développé de l'attribut spécifié et retourne l'objet <xref:System.Xml.Linq.XAttribute> correspondant ou `null` s'il n'existe aucun attribut avec le nom spécifié.  
  
## Notes  
 Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XElement.Attribute%2A> de la classe <xref:System.Xml.Linq.XElement?displayProperty=fullName>.  
  
## Voir aussi  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valeur](../designers/value-xattribute-dynamic-property.md)