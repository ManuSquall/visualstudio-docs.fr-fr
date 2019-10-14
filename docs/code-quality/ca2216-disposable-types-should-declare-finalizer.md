---
title: 'CA2216 : Les types pouvant être supprimés doivent déclarer un finaliseur'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisposableTypesShouldDeclareFinalizer
- CA2216
helpviewer_keywords:
- CA2216
- DisposableTypesShouldDeclareFinalizer
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ac52bdb17aeb7d04e434d2b02ff9a905eab49a2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305919"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216 : Les types pouvant être supprimés doivent déclarer un finaliseur

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Catégorie|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type qui implémente <xref:System.IDisposable?displayProperty=fullName> et a des champs qui suggèrent l’utilisation de ressources non managées, n’implémente pas de finaliseur comme décrit par <xref:System.Object.Finalize%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle

Une violation de cette règle est signalée si le type jetable contient des champs des types suivants :

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, implémentez un finaliseur qui appelle votre méthode <xref:System.IDisposable.Dispose%2A>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle si le type n’implémente pas <xref:System.IDisposable> pour libérer des ressources non managées.

## <a name="example"></a>Exemple

L’exemple suivant montre un type qui viole cette règle.

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>Règles associées

@NO__T 0CA2115 : Appelez GC. KeepAlive quand vous utilisez des ressources natives @ no__t-0

@NO__T 0CA1816 : Appelez GC. SuppressFinalize correctement @ no__t-0

@NO__T 0CA1049 : Les types qui possèdent des ressources natives doivent être supprimables @ no__t-0

## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)