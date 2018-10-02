---
title: Éléments (Propriété dynamique XElement) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: 75cb7f8f6a5259151679ecee84bbeb5db336782f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47495629"
---
# <a name="elements-xelement-dynamic-property"></a>Éléments (Propriété dynamique XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [éléments (propriété dynamique XElement)](https://docs.microsoft.com/visualstudio/designers/elements-xelement-dynamic-property).  
  
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



