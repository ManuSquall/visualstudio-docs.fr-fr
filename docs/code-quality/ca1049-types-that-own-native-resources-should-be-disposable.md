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
ms.openlocfilehash: a39d1e03da062f3030571820e98898d5122d495f
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349098"
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049 : Les types qui possèdent des ressources natives doivent être supprimables

|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type fait référence à un champ <xref:System.IntPtr?displayProperty=fullName>, à un champ <xref:System.UIntPtr?displayProperty=fullName> ou à un champ <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>, mais il n’implémente pas <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle

Cette règle suppose que les champs <xref:System.IntPtr>, <xref:System.UIntPtr> et <xref:System.Runtime.InteropServices.HandleRef> stockent des pointeurs vers des ressources non managées. Les types qui allouent des ressources non managées doivent implémenter <xref:System.IDisposable> pour permettre aux appelants de libérer ces ressources à la demande et de raccourcir les durées de vie des objets qui contiennent les ressources.

Le modèle de conception recommandé pour nettoyer les ressources non managées consiste à fournir un moyen implicite et explicite pour libérer ces ressources à l’aide de la méthode <xref:System.Object.Finalize%2A?displayProperty=fullName> et de la méthode <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>, respectivement. Le garbage collector appelle la méthode <xref:System.Object.Finalize%2A> d’un objet à un moment indéterminé une fois que l’objet est considéré comme n’étant plus accessible. Après l’appel de <xref:System.Object.Finalize%2A>, un garbage collection supplémentaire est requis pour libérer l’objet. La méthode <xref:System.IDisposable.Dispose%2A> permet à l’appelant de libérer explicitement des ressources à la demande, avant que les ressources ne soient libérées si elles étaient laissées au garbage collector. Après le nettoyage des ressources non managées, <xref:System.IDisposable.Dispose%2A> doit appeler la méthode <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> pour permettre au garbage collector de savoir que <xref:System.Object.Finalize%2A> n’a plus à être appelé ; Cela élimine le besoin de la garbage collection supplémentaire et raccourcit la durée de vie de l’objet.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, implémentez <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle si le type ne fait pas référence à une ressource non managée. Sinon, ne supprimez pas un avertissement de cette règle, car l’échec de l’implémentation de <xref:System.IDisposable> peut entraîner l’indisponibilité ou la sous-utilisation des ressources non managées.

## <a name="example"></a>Exemple
L’exemple suivant illustre un type qui implémente <xref:System.IDisposable> pour nettoyer une ressource non managée.

[!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
[!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Règles associées
[CA2115 : Appelez GC.KeepAlive lorsque vous utilisez des ressources natives](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

[CA1816 : Appelez GC.SuppressFinalize correctement](../code-quality/ca1816.md)

[CA2216 : Les types supprimables doivent déclarer un finaliseur](../code-quality/ca2216.md)

[CA1001 : Les types qui ont des champs supprimables doivent être supprimables](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Voir aussi

- [Nettoyage de ressources non managées](/dotnet/standard/garbage-collection/unmanaged)
- [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)