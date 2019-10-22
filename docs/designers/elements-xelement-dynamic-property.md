---
title: Éléments (Propriété dynamique XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d92e9ebd1e5be9f3535dcac136bb46ba33975f0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637322"
---
# <a name="elements-xelement-dynamic-property"></a>Éléments (Propriété dynamique XElement)

Obtient un indexeur utilisé pour récupérer les éléments enfants de l’élément actif qui correspondent au nom développé spécifié.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Elements[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Indexeur de type `IEnumerable<XElement> Item(String expandedName)`. Cet indexeur prend le nom développé des éléments enfants souhaités et retourne les éléments enfants correspondants dans une collection <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.

## <a name="remarks"></a>Notes

Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XContainer.Elements(System.Xml.Linq.XName)?displayProperty=fullName> de la classe <xref:System.Xml.Linq.XContainer>.

Les éléments de la collection retournée sont spécifiés dans l’ordre du document source XML.

Cette propriété utilise l'exécution différée.

## <a name="see-also"></a>Voir aussi

- [Propriétés dynamiques de la classe XElement](../designers/attribute-xelement-dynamic-property.md)
- [Élément](../designers/element-xelement-dynamic-property.md)
- [Descendants](../designers/descendants-xelement-dynamic-property.md)