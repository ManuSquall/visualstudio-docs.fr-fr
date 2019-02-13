---
title: Xml (propriété dynamique XElement)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d58dea02a45ccc84e7829da2acdb479eb17dda3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931245"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (propriété dynamique XElement)

Obtient le contenu XML sans mise en forme de l'élément.

## <a name="syntax"></a>Syntaxe

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

<xref:System.String> qui représente le contenu XML sans mise en forme de l'élément.

## <a name="remarks"></a>Notes

Cette propriété est équivalente à la méthode <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> de la classe <xref:System.Xml.Linq.XNode?displayProperty=fullName>, avec le paramètre `SaveOptions` défini à la valeur <xref:System.Xml.Linq.SaveOptions>.

## <a name="see-also"></a>Voir aussi

- [Propriétés dynamiques de la classe XElement](../designers/xelement-class-dynamic-properties.md)
- [Valeur](../designers/value-xelement-dynamic-property.md)