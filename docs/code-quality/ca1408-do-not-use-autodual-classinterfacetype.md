---
title: 'CA1408 : Ne pas utiliser le paramètre AutoDual ClassInterfaceType'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 142d011ff73fbaf03af62164f962470f8feb3246
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440392"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408 : Ne pas utiliser le paramètre AutoDual ClassInterfaceType

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Un type visible COM (Component Object Model) est marqué avec l’attribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> défini sur la valeur `AutoDual` de <xref:System.Runtime.InteropServices.ClassInterfaceType>.

## <a name="rule-description"></a>Description de la règle
Les types qui utilisent une interface double permettent aux clients de se lier à une disposition d'interface spécifique. Les modifications apportées à une version future de la disposition du type ou des types de base bloquent les clients COM qui se lient à l'interface. Par défaut, si l’attribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> n’est pas spécifié, une interface de dispatch uniquement est utilisée.

Sauf indication contraire, tous les types non génériques publics sont visibles par COM ; tous les types non publics et génériques sont invisibles pour COM.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, remplacez la valeur de l’attribut <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> par la valeur `None` de <xref:System.Runtime.InteropServices.ClassInterfaceType> et définissez explicitement l’interface.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez pas un avertissement de cette règle à moins qu’il ne soit certain que la disposition du type et de ses types de base ne changera pas dans une version ultérieure.

## <a name="example"></a>Exemple
L’exemple suivant montre une classe qui enfreint la règle et une nouvelle déclaration de la classe pour utiliser une interface explicite.

[!code-csharp[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/CSharp/ca1408-do-not-use-autodual-classinterfacetype_1.cs)]
[!code-vb[FxCop.Interoperability.AutoDual#1](../code-quality/codesnippet/VisualBasic/ca1408-do-not-use-autodual-classinterfacetype_1.vb)]

## <a name="related-rules"></a>Règles associées
[CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

[CA1412 : Marquez les interfaces ComSource comme IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Voir aussi

- [Qualifier des types .NET pour l'interopérabilité](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interopération avec du code non managé](/dotnet/framework/interop/index)
