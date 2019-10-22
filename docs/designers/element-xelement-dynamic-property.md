---
title: Element (propriété dynamique XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08b2f7f008c1522c5f65b5ee7a58c3ed98e8a845
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637327"
---
# <a name="element-xelement-dynamic-property"></a>Element (propriété dynamique XElement)

Obtient un indexeur utilisé pour récupérer l'instance d'élément enfant qui correspond au nom développé spécifié.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Indexeur de type `XElement Item(String expandedName)`. Cet indexeur prend un paramètre de nom développé et retourne l'objet <xref:System.Xml.Linq.XElement> correspondant ou `null` s'il n'existe aucun élément avec le nom spécifié.

## <a name="remarks"></a>Notes

Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XContainer.Element%2A> de la classe <xref:System.Xml.Linq.XContainer?displayProperty=fullName>.

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Propriétés dynamiques de la classe XElement](../designers/attribute-xelement-dynamic-property.md)
- [Élements](../designers/elements-xelement-dynamic-property.md)