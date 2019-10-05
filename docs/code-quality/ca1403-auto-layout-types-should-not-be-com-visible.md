---
title: 'CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4e590514247444d32d0d9a31b2bbc409434cf53c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234832"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un type valeur visible com (Component Object Model) est marqué avec l' <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> attribut défini sur <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle

<xref:System.Runtime.InteropServices.LayoutKind>les types de disposition sont gérés par le common language runtime. La disposition de ces types peut changer entre les versions de .NET, ce qui interrompt les clients COM qui attendent une disposition spécifique. Si l' <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut n’est pas spécifié, C#les compilateurs, C++ Visual Basic et spécifient [LayoutKind. auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) pour les types valeur.

Sauf indication contraire, tous les types publics et non génériques sont visibles par COM, et tous les types non publics et génériques sont invisibles pour COM. Toutefois, pour réduire les faux positifs, cette règle exige que la visibilité COM du type soit explicitement indiquée. L’assembly conteneur doit être marqué avec <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> le défini `false` sur et le type doit être marqué avec <xref:System.Runtime.InteropServices.ComVisibleAttribute> le défini `true`sur.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, remplacez la valeur de l' <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut par [LayoutKind. Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) ou [LayoutKind. sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>), ou rendez le type invisible pour com.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple

L’exemple suivant montre un type qui viole la règle et un type qui satisfait la règle.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Règles associées

[CA1408 Ne pas utiliser la double](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Voir aussi

- [Qualifier les types .NET pour l’interopérabilité](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interagir avec du code non managé](/dotnet/framework/interop/index)