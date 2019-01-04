---
title: 'CA2216 : Les types supprimables doivent déclarer un finaliseur'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f53f91a6a4775fb17e273fb87c4c669f74ad45e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825995"
---
# <a name="ca2216-disposable-types-should-declare-finalizer"></a>CA2216 : Les types supprimables doivent déclarer un finaliseur

|||
|-|-|
|TypeName|DisposableTypesShouldDeclareFinalizer|
|CheckId|CA2216|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type qui implémente <xref:System.IDisposable?displayProperty=fullName>et comporte des champs qui laissent entendre l’utilisation des ressources non managées, n’implémente pas de finaliseur comme décrit par <xref:System.Object.Finalize%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle

Une violation de cette règle est signalée si le type supprimable contient des champs des types suivants :

- <xref:System.IntPtr?displayProperty=fullName>

- <xref:System.UIntPtr?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, implémentez un finaliseur qui appelle votre <xref:System.IDisposable.Dispose%2A> (méthode).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle si le type n’implémente pas <xref:System.IDisposable> en vue de libérer des ressources non managées.

## <a name="example"></a>Exemple

L’exemple suivant illustre un type qui enfreint cette règle.

[!code-csharp[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]

## <a name="related-rules"></a>Règles associées

[CA2115 : Appelez GC. KeepAlive lors de l’utilisation des ressources natives](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816 : Appelez GC. SuppressFinalize correctement](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA1049 : Les types qui possèdent des ressources natives doivent être supprimables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.IDisposable?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)