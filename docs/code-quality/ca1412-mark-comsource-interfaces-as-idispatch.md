---
title: 'CA1412 : Marquer les interfaces ComSource comme IDispatch'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: caaae787d5e4801f3fc3b8d881b386595fb2eca4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234690"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412 : Marquer les interfaces ComSource comme IDispatch

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un type est marqué avec l' <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> attribut et au moins une interface spécifiée n’est pas marquée <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> avec l’attribut défini sur `InterfaceIsDispatch` la valeur.

## <a name="rule-description"></a>Description de la règle

<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>est utilisé pour identifier les interfaces d’événement qu’une classe expose aux clients COM (Component Object Model). Ces interfaces doivent être exposées comme `InterfaceIsIDispatch` pour permettre à Visual Basic 6 clients com de recevoir des notifications d’événements. Par défaut, si une interface n’est pas marquée avec <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> l’attribut, elle est exposée en tant qu’interface double.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, ajoutez ou modifiez l' <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> attribut afin que sa valeur soit définie sur InterfaceIsIDispatch pour toutes les interfaces spécifiées avec l' <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> attribut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple

L’exemple suivant montre une classe dans laquelle l’une des interfaces enfreint la règle.

[!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/CSharp/ca1412-mark-comsource-interfaces-as-idispatch_1.cs)]
[!code-vb[FxCop.Interoperability.MarkIDispatch#1](../code-quality/codesnippet/VisualBasic/ca1412-mark-comsource-interfaces-as-idispatch_1.vb)]

## <a name="related-rules"></a>Règles associées

[CA1408 Ne pas utiliser la double](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Voir aussi

- [Interopération avec du code non managé](/dotnet/framework/interop/index)