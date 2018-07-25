---
title: Descendants (propriété dynamique XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7255753445d014b1ab59f6e2e8143b341b28a892
ms.sourcegitcommit: 522ba712c0d625e51352506146b0556414681964
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37890251"
---
# <a name="descendants-xelement-dynamic-property"></a>Descendants (propriété dynamique XElement)

Obtient un indexeur utilisé pour récupérer tous les éléments descendants de l’élément actif qui correspondent au nom développé spécifié.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Descendants[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

Indexeur de type `IEnumerable<XElement> Item(String expandedName)`. Cet indexeur prend le nom développé des éléments descendants spécifiés et retourne les éléments enfants correspondants dans une collection <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`.

## <a name="remarks"></a>Notes

Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XContainer.Descendants(System.Xml.Linq.XName)?displayProperty=fullName> de la classe <xref:System.Xml.Linq.XContainer>.

Les éléments de la collection retournée sont spécifiés dans l’ordre du document source XML.

Cette propriété utilise l'exécution différée.

## <a name="see-also"></a>Voir aussi

- [Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Élements](../designers/elements-xelement-dynamic-property.md)