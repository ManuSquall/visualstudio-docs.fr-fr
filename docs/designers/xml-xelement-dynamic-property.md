---
title: Xml (propriété dynamique XElement)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a69245a875d0c1df1942af12afaacc5a9ffc34b
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080835"
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