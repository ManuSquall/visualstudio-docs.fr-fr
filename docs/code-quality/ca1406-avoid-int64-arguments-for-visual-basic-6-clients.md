---
title: 'CA1406 : Éviter les arguments Int64 pour les clients Visual Basic 6'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 82a8b1ea389c37dc63a9fe7366208a2a3028efb8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234798"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406 : Éviter les arguments Int64 pour les clients Visual Basic 6

|||
|-|-|
|TypeName|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Un type qui est spécifiquement marqué comme visible par le modèle COM (Component Object Model) déclare un membre qui accepte <xref:System.Int64?displayProperty=fullName> un argument.

## <a name="rule-description"></a>Description de la règle
Les clients COM Visual Basic 6 ne peut pas accéder aux entiers de 64 bits.

Par défaut, les éléments suivants sont visibles par COM : assemblys, les types publics, les membres d’instance publics dans les types publics et tous les membres des types valeur publics. Toutefois, pour réduire les faux positifs, cette règle exige que la visibilité COM du type soit explicitement indiquée. l’assembly conteneur doit être marqué avec <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> le défini `false` sur et le type doit être marqué avec <xref:System.Runtime.InteropServices.ComVisibleAttribute> le défini `true`sur.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle pour un paramètre dont la valeur peut toujours être exprimée sous la forme d’un entier 32 bits, remplacez le <xref:System.Int32?displayProperty=fullName>type de paramètre par. Si la valeur du paramètre peut être supérieure à celle qui peut être exprimée sous la forme d’un entier 32 bits, remplacez le <xref:System.Decimal?displayProperty=fullName>type de paramètre par. Notez que <xref:System.Single?displayProperty=fullName> et <xref:System.Double?displayProperty=fullName> perdent <xref:System.Int64> la précision aux plages supérieures du type de données. Si le membre n’est pas destiné à être visible par com, marquez- <xref:System.Runtime.InteropServices.ComVisibleAttribute> le avec `false`la valeur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle s’il est certain que Visual Basic 6 clients COM n’accèdent pas au type.

## <a name="example"></a>Exemple
L’exemple suivant montre un type qui viole la règle.

[!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
[!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Règles associées
[CA1413 Éviter les champs non publics dans les types valeur visibles par COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407 Éviter les membres statiques dans les types visibles par COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017 Marquer les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Voir aussi

- [Interopération avec du code non managé](/dotnet/framework/interop/index)
- [Long (type de données)](/dotnet/visual-basic/language-reference/data-types/long-data-type)