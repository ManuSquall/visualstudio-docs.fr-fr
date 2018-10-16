---
title: Éléments (Propriété dynamique XElement) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- XElement.Elements
api_type:
- Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b65f32cc4146f275ec77a5942bdfef3fcf493b8b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237287"
---
# <a name="elements-xelement-dynamic-property"></a>Éléments (Propriété dynamique XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtient un indexeur utilisé pour récupérer les éléments enfants de l’élément actif qui correspondent au nom développé spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
elem.Elements[{namespaceName}localName]   
```  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 Indexeur de type `IEnumerable<XElement> Item(String expandedName)`. Cet indexeur prend le nom développé des éléments enfants souhaités et retourne les éléments enfants correspondants dans une collection <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.  
  
## <a name="remarks"></a>Notes  
 Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XContainer.Elements%28System.Xml.Linq.XName%29?displayProperty=fullName> de la classe <xref:System.Xml.Linq.XContainer>.  
  
 Les éléments de la collection retournée sont spécifiés dans l'ordre du document source XML.  
  
 Cette propriété utilise l'exécution différée.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)   
 [Élément](../designers/element-xelement-dynamic-property.md)   
 [Descendants](../designers/descendants-xelement-dynamic-property.md)



