---
title: "Propri&#233;t&#233;s dynamiques de LINQ to XML  | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Propri&#233;t&#233;s dynamiques de LINQ to XML 
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette section fournit des informations de référence sur les propriétés dynamiques dans LINQ to XML.Plus spécifiquement, ces propriétés sont exposées par les classes <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XElement>, qui sont dans l'espace de noms <xref:System.Xml.Linq>.  
  
 Comme expliqué dans la rubrique [Vue d'ensemble de la liaison de données WPF avec LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), chacune des propriétés dynamiques est équivalente à une méthode ou propriété publique standard dans la même classe.Ces membres standard doivent être utilisés dans la plupart des cas ; des propriétés dynamiques sont fournies spécifiquement pour les scénarios de liaison de données LINQ to XML.Pour plus d'informations sur les membres standard de ces classes, consultez les rubriques de référence <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XElement>.  
  
 En ce qui concerne leurs valeurs résolues, les propriétés dynamiques dans cette section se répartissent en deux catégories :  
  
-   Les propriétés simples, telles que les propriétés `Value` dans les classes <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XElement>, qui sont résolues à une valeur unique.  
  
-   Les valeurs indexées, telles que les propriétés [Elements](../designers/elements-xelement-dynamic-property.md) et [Descendants](../designers/descendants-xelement-dynamic-property.md) de l'objet <xref:System.Xml.Linq.XElement>, qui sont résolues à un type d'indexeur.Pour que les types d'indexeur soient résolus à la valeur ou collection souhaitée, un paramètre de nom étendu doit leur être passé.  
  
 Toutes les propriétés dynamiques qui retournent une valeur indexée de type <xref:System.Collections.Generic.IEnumerable%601> utilisent l'exécution différée.Pour plus d'informations sur l'exécution différée, consultez [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries).  
  
## Dans cette section  
  
|Rubrique|Description|  
|--------------|-----------------|  
|[Propriétés dynamiques de la classe XAttribute](../designers/xattribute-class-dynamic-properties.md)|Fournit des détails sur les propriétés dynamiques exposées par la classe <xref:System.Xml.Linq.XAttribute>.|  
|[Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)|Fournit des détails sur les propriétés dynamiques exposées par la classe <xref:System.Xml.Linq.XElement>.|  
  
## Référence  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## Voir aussi  
 [Liaison de données WPF avec LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Vue d'ensemble de la liaison de données WPF avec LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)