---
title: 'CA2104 : Ne déclarez pas les types référence mutables en lecture seule'
ms.date: 11/01/2018
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8f4f165b4b00f46b478907c9affca672b4c7f113
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232954"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104 : Ne déclarez pas les types référence mutables en lecture seule

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

> [!NOTE]
> La règle CA2104 est obsolète et sera supprimée dans une future version de Visual Studio. Elle ne sera pas implémentée en tant qu' [analyseur](roslyn-analyzers-overview.md) en raison de l’analyse complexe requise pour déterminer l’immuabilité réelle d’un type.

## <a name="cause"></a>Cause

Un type visible de l’extérieur contient un champ en lecture seule visible de l’extérieur qui constitue un type référence mutable.

## <a name="rule-description"></a>Description de la règle

Un type mutable est un type dont les données d’instance peuvent être modifiées. La <xref:System.Text.StringBuilder?displayProperty=fullName> classe est un exemple de type référence mutable. Il contient des membres qui peuvent modifier la valeur d’une instance de la classe. La <xref:System.String?displayProperty=fullName> classe est un exemple de type de référence immuable. Une fois qu’elle a été instanciée, sa valeur ne peut jamais changer.

Le modificateur en lecture seule ([ReadOnly](/dotnet/csharp/language-reference/keywords/readonly) en C#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) en Visual Basic et [const](/cpp/cpp/const-cpp) dans C++) sur un champ de type référence (ou pointeur dans C++) empêche le champ d’être remplacé par une autre instance du type référence. Toutefois, le modificateur n’empêche pas les données d’instance du champ d’être modifiées par le biais du type référence.

Cette règle peut afficher par inadvertance une violation pour un type qui est, en fait, immuable. Dans ce cas, il est possible de supprimer l’avertissement.

Les champs de tableau en lecture seule sont exemptés de cette règle, mais provoquent [une violation de la CA2105 : Les champs de tableau ne doivent pas](../code-quality/ca2105-array-fields-should-not-be-read-only.md) être en lecture seule.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez le modificateur en lecture seule ou, si une modification avec rupture est acceptable, remplacez le champ par un type immuable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle si le type de champ est immuable.

## <a name="example"></a>Exemple

L’exemple suivant montre une déclaration de champ qui provoque une violation de cette règle :

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]