---
title: "Xml (propri&#233;t&#233; dynamique XElement) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XElement.Xml"
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Xml (propri&#233;t&#233; dynamique XElement)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Obtient le contenu XML sans mise en forme de l'élément.  
  
## Syntaxe  
  
```  
elem.Xml  
```  
  
## Valeur de propriété\/valeur de retour  
 <xref:System.String> qui représente le contenu XML sans mise en forme de l'élément.  
  
## Notes  
 Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> de la classe <xref:System.Xml.Linq.XNode?displayProperty=fullName>, avec le paramètre `SaveOptions` défini à la valeur <xref:System.Xml.Linq.SaveOptions>.  
  
## Voir aussi  
 [Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valeur](../designers/value-xelement-dynamic-property.md)