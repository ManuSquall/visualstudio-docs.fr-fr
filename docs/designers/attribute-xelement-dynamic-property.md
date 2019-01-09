---
title: Attribute (propriété dynamique XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 701636a82b07311bdc9f5a9b20882d613e8469ce
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959919"
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