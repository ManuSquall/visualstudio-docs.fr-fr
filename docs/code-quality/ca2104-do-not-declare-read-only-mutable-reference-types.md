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
ms.openlocfilehash: 40fdeefc2d664b80bb6e17c109349cb5912b0516
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077704"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104 : Ne déclarez pas les types référence mutables en lecture seule

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

> [!NOTE]
> CA2104 de règle est obsolète et sera supprimée dans une future version de Visual Studio. Elle n’est pas implémentée comme un [analyseur](roslyn-analyzers-overview.md) en raison de l’analyse complexe qui est nécessaire pour déterminer l’immuabilité réelle d’un type.

## <a name="cause"></a>Cause

Un type visible de l’extérieur contient un champ en lecture seule visible de l’extérieur qui constitue un type référence mutable.

## <a name="rule-description"></a>Description de la règle

Un type mutable est un type dont les données d’instance peuvent être modifiées. Le <xref:System.Text.StringBuilder?displayProperty=fullName> classe est un exemple d’un type référence mutable. Il contient des membres qui peuvent modifier la valeur d’une instance de la classe. Un exemple d’un type référence immuable est le <xref:System.String?displayProperty=fullName> classe. Une fois qu’il a été instancié, sa valeur ne peut jamais changer.

Le modificateur en lecture seule ([readonly](/dotnet/csharp/language-reference/keywords/readonly) dans C#, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) en Visual Basic, et [const](/cpp/cpp/const-cpp) en C++) sur un type référence, champ (ou un pointeur en C++) empêche le champ à partir de remplacée par une autre instance du type référence. Toutefois, le modificateur n’empêche pas les données d’instance du champ d’être modifiées par le type de référence.

Cette règle peut par inadvertance indiquer une violation pour un type qui est en fait, immuable. Dans ce cas, il est possible de supprimer l’avertissement sans.

Champs de tableau en lecture seule sont exemptés de cette règle, mais au lieu de cela provoque une violation de la [CA2105 : Champs de tableau ne doivent pas être en lecture seule](../code-quality/ca2105-array-fields-should-not-be-read-only.md) règle.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez le modificateur en lecture seule ou, si une modification avec rupture est acceptable, remplacez le champ par un type immuable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle si le type de champ est immuable.

## <a name="example"></a>Exemple

L’exemple suivant montre une déclaration de champ qui provoque une violation de cette règle :

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]