---
title: "Attribute (propriété dynamique XElement) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0fd01945c2a33f3929f59e66a02a1d08a39c3cc7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (propriété dynamique XElement)
Obtient un indexeur utilisé pour récupérer l’instance d’attribut qui correspond au nom développé spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Indexeur de type `XAttribute Item(String expandedName)`. Cet indexeur prend le nom développé de l'attribut spécifié et retourne l'objet <xref:System.Xml.Linq.XAttribute> correspondant ou `null` s'il n'existe aucun attribut avec le nom spécifié.  
  
## <a name="remarks"></a>Remarques  
 Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XElement.Attribute%2A> de la classe <xref:System.Xml.Linq.XElement?displayProperty=fullName>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Valeur](../designers/value-xattribute-dynamic-property.md)