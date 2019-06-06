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
ms.openlocfilehash: ef7b693a881aaa1457004c84968ebc80936fc2b2
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714846"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM

|||
|-|-|
|TypeName|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un type de valeur visible du composant COM (Object Model) est marqué avec le <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> attribut la valeur <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle

<xref:System.Runtime.InteropServices.LayoutKind> les types de disposition sont gérés par le common language runtime. La disposition de ces types peut varier entre les versions de .NET, ce qui interrompt les clients COM qui attendent une disposition spécifique. Si le <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut n’est pas spécifié, les compilateurs c#, Visual Basic et C++ spécifient [valeur LayoutKind.Auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) pour les types valeur.

Sauf mention contraire, tous les types publics, non génériques sont visibles par COM, et tous les types non publics et génériques ne sont pas visibles par COM. Toutefois, pour réduire les faux positifs, cette règle requiert que la visibilité COM du type d’être explicitement spécifié. L’assembly conteneur doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> définie sur `false` et le type doit être marqué avec le <xref:System.Runtime.InteropServices.ComVisibleAttribute> défini sur `true`.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, modifiez la valeur de la <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribut [LayoutKind.Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) ou [LayoutKind.Sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>), ou rendez le type invisible à COM.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple

L’exemple suivant montre un type qui viole la règle et un type qui satisfait la règle.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Règles associées

[CA1408 : Ne pas utiliser AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Voir aussi

- [Qualifier des types .NET pour l’interopérabilité](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interagir avec le code non managé](/dotnet/framework/interop/index)