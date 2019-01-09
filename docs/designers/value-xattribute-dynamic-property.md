---
title: Value (propriété dynamique XAttribute)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2b97e33bdcb28a3c8790af752d5ab9786dc5ef3d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882891"
---
# <a name="value-xattribute-dynamic-property"></a>Value (propriété dynamique XAttribute)

Obtient ou définit la valeur de l'attribut XML.

## <a name="syntax"></a>Syntaxe

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour

<xref:System.String> contenant la valeur de cet attribut.

## <a name="exceptions"></a>Exceptions

|Type d'exception|Condition|
| - |---------------|
|<xref:System.ArgumentNullException>|Lors de la définition, `value` a la valeur `null`.|

## <a name="remarks"></a>Notes

Cette propriété est équivalente à la propriété <xref:System.Xml.Linq.XAttribute.Value%2A> de la classe <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, mais cette propriété dynamique prend également en charge les notifications de changement.

## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Propriétés dynamiques de la classe XAttribute](../designers/xattribute-class-dynamic-properties.md)
- [Attribut](../designers/attribute-xelement-dynamic-property.md)