---
title: 'CA1049 : Les types qui possèdent des ressources natives doivent être supprimables'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1049
- TypesThatOwnNativeResourcesShouldBeDisposable
helpviewer_keywords:
- TypesThatOwnNativeResourcesShouldBeDisposable
- CA1049
ms.assetid: 084e587d-0e45-4092-b767-49eed30d6a35
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- cplusplus
ms.openlocfilehash: ef7b72eade7ea8e4486d5c317c06026bb4d0b95f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235741"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049 : Les types qui possèdent des ressources natives doivent être supprimables

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type fait référence <xref:System.IntPtr?displayProperty=fullName> à un champ <xref:System.UIntPtr?displayProperty=fullName> , à un champ <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> ou à un champ, mais <xref:System.IDisposable?displayProperty=fullName>n’implémente pas.

## <a name="rule-description"></a>Description de la règle

Cette règle suppose que <xref:System.IntPtr>les champs, et <xref:System.Runtime.InteropServices.HandleRef> stockent des pointeurs vers des <xref:System.UIntPtr>ressources non managées. Les types qui allouent des ressources non managées doivent implémenter <xref:System.IDisposable> pour permettre aux appelants de libérer ces ressources à la demande et de raccourcir les durées de vie des objets qui contiennent les ressources.

Le modèle de conception recommandé pour nettoyer les ressources non managées consiste à fournir un moyen implicite et explicite pour libérer ces ressources à l’aide <xref:System.Object.Finalize%2A?displayProperty=fullName> de la méthode <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> et de la méthode, respectivement. Le garbage collector appelle la <xref:System.Object.Finalize%2A> méthode d’un objet à un moment indéterminé une fois que l’objet est considéré comme n’étant plus accessible. Après <xref:System.Object.Finalize%2A> l’appel de, une garbage collection supplémentaire est nécessaire pour libérer l’objet. La <xref:System.IDisposable.Dispose%2A> méthode permet à l’appelant de libérer explicitement des ressources à la demande, avant que les ressources ne soient libérées si elles étaient laissées au garbage collector. Après le nettoyage des ressources non managées, <xref:System.IDisposable.Dispose%2A> doit appeler la <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> méthode pour permettre au garbage collector de savoir qu' <xref:System.Object.Finalize%2A> il n’est plus nécessaire d’appeler. cela élimine la nécessité de l’garbage collection supplémentaire et raccourcit le durée de vie de l’objet.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, implémentez <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle si le type ne fait pas référence à une ressource non managée. Sinon, ne supprimez pas un avertissement de cette règle, car l' <xref:System.IDisposable> échec de l’implémentation peut entraîner l’indisponibilité ou la sous-utilisation des ressources non managées.

## <a name="example"></a>Exemple
L’exemple suivant montre un type qui implémente <xref:System.IDisposable> pour nettoyer une ressource non managée.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Règles associées
[CA2115 Appelez GC. KeepAlive quand vous utilisez des ressources natives](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816 Appelez GC. SuppressFinalize correctement](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

[CA2216 Les types jetables doivent déclarer un finaliseur](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA1001 : Les types qui possèdent des champs supprimables doivent être supprimables](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Voir aussi

- [Nettoyage de ressources non managées](/dotnet/standard/garbage-collection/unmanaged)
- [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)