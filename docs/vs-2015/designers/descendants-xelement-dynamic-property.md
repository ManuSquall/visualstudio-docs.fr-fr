---
title: Descendants (propriété dynamique XElement) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b0496a04219c88573b3b555ef879a046d90faa3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664784"
---
# <a name="descendants-xelement-dynamic-property"></a>Descendants (propriété dynamique XElement)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtient un indexeur utilisé pour récupérer tous les éléments descendants de l’élément actif qui correspondent au nom développé spécifié.

## <a name="syntax"></a>Syntaxe

```
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour
 Indexeur de type `IEnumerable<XElement> Item(String expandedName)`. Cet indexeur prend le nom développé des éléments descendants spécifiés et retourne les éléments enfants correspondants dans une collection <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.

## <a name="remarks"></a>Notes
 Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName> de la classe <xref:System.Xml.Linq.XContainer>.

 Les éléments de la collection retournée sont spécifiés dans l’ordre du document source XML.

 Cette propriété utilise l'exécution différée.

## <a name="see-also"></a>Voir aussi
 [Éléments](../designers/elements-xelement-dynamic-property.md) de [propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)
