---
title: Value (propriété dynamique XAttribute) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9a31b4c4182ed67a3e67d3c25c2c5ccf50e083f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664047"
---
# <a name="value-xattribute-dynamic-property"></a>Value (propriété dynamique XAttribute)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obtient ou définit la valeur de l'attribut XML.

## <a name="syntax"></a>Syntaxe

```
attrib.Value
```

## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour
 <xref:System.String> contenant la valeur de cet attribut.

## <a name="exceptions"></a>Exceptions

|Type d'exception|Condition|
|--------------------|---------------|
|<xref:System.ArgumentNullException>|Lors de la définition, `value` a la valeur `null`.|

## <a name="remarks"></a>Notes
 Cette propriété est équivalente à la propriété <xref:System.Xml.Linq.XAttribute.Value%2A> de la classe <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>, mais cette propriété dynamique prend également en charge les notifications de changement.

## <a name="see-also"></a>Voir aussi
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>[Attribut](../designers/attribute-xelement-dynamic-property.md) de [propriétés dynamiques de la classe XAttribute](../designers/xattribute-class-dynamic-properties.md)
