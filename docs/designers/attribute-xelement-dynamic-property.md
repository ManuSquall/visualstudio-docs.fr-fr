---
title: Attribute (propriété dynamique XElement)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ec27fe2d7824ca32cbf97dbabac8b7ea6c4aed6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948496"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (propriété dynamique XElement)

Obtient un indexeur utilisé pour récupérer l’instance d’attribut qui correspond au nom développé spécifié.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Indexeur de type `XAttribute Item(String expandedName)`. Cet indexeur prend le nom développé de l’attribut spécifié et retourne l’objet <xref:System.Xml.Linq.XAttribute> correspondant ou `null` s’il n’existe aucun attribut avec le nom spécifié.

## <a name="remarks"></a>Notes

Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XElement.Attribute%2A> de la classe <xref:System.Xml.Linq.XElement?displayProperty=fullName>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Valeur](../designers/value-xattribute-dynamic-property.md)