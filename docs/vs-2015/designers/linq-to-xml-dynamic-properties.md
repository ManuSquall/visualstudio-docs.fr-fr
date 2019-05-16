---
title: Propriétés dynamiques LINQ to XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 0455f47c-4a68-4f2e-a3f8-dd1d85b99012
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1aed85754eb1238528af9b5d74f2369b2548edc0
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687170"
---
# <a name="linq-to-xml-dynamic-properties"></a>Propriétés dynamiques LINQ to XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette section fournit des informations de référence sur les propriétés dynamiques dans LINQ to XML. Plus spécifiquement, ces propriétés sont exposées par les classes <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XElement>, qui sont dans l'espace de noms <xref:System.Xml.Linq>.  
  
 Comme expliqué dans la rubrique [Vue d’ensemble de la liaison de données WPF avec LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md), chacune des propriétés dynamiques est équivalente à une méthode ou propriété publique standard dans la même classe. Ces membres standard doivent être utilisés dans la plupart des cas ; des propriétés dynamiques sont fournies spécifiquement pour les scénarios de liaison de données LINQ to XML. Pour plus d'informations sur les membres standard de ces classes, consultez les rubriques de référence <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XElement>.  
  
 En ce qui concerne leurs valeurs résolues, les propriétés dynamiques dans cette section se répartissent en deux catégories :  
  
- Les propriétés simples, telles que les propriétés `Value` dans les classes <xref:System.Xml.Linq.XAttribute> et <xref:System.Xml.Linq.XElement>, qui sont résolues à une valeur unique.  
  
- Les valeurs indexées, telles que les propriétés [Elements](../designers/elements-xelement-dynamic-property.md) et [Descendants](../designers/descendants-xelement-dynamic-property.md) de l’objet <xref:System.Xml.Linq.XElement>, qui sont résolues en un type d’indexeur. Pour que les types d’indexeur soient résolus à la valeur ou collection souhaitée, un paramètre de nom étendu doit leur être passé.  
  
  Toutes les propriétés dynamiques qui retournent une valeur indexée de type <xref:System.Collections.Generic.IEnumerable%601> utilisent l'exécution différée. Pour plus d’informations sur l’exécution différée, consultez [Introduction aux requêtes LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8).  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Propriétés dynamiques de la classe XAttribute](../designers/xattribute-class-dynamic-properties.md)|Fournit des détails sur les propriétés dynamiques exposées par la classe <xref:System.Xml.Linq.XAttribute>.|  
|[Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)|Fournit des détails sur les propriétés dynamiques exposées par la classe <xref:System.Xml.Linq.XElement>.|  
  
## <a name="reference"></a>Référence  
 <xref:System.Xml.Linq>  
  
 <xref:System.Xml.Linq.XElement?displayProperty=fullName>  
  
 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison de données WPF avec LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml.md)   
 [Vue d’ensemble de la liaison de données WPF avec LINQ to XML](../designers/wpf-data-binding-with-linq-to-xml-overview.md)   
 [Introduction aux requêtes LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)
