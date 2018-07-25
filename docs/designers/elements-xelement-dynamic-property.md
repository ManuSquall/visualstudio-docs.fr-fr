---
title: Éléments (Propriété dynamique XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Elements
apitype: Assembly
ms.assetid: 3d5737f2-d2ed-410a-821c-349dbb2b574f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c78dece049aa2d446a0f03b24f3e2c2640131327
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924409"
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

- [Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Élément](../designers/element-xelement-dynamic-property.md)
- [Descendants](../designers/descendants-xelement-dynamic-property.md)