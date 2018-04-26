---
title: 'CA1049 : Les types qui possèdent des ressources natives doivent être supprimables'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 0f96f737274204018be3b30aaa4d85e07cc59f53
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1049-types-that-own-native-resources-should-be-disposable"></a>CA1049 : Les types qui possèdent des ressources natives doivent être supprimables
|||
|-|-|
|TypeName|TypesThatOwnNativeResourcesShouldBeDisposable|
|CheckId|CA1049|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type référence un <xref:System.IntPtr?displayProperty=fullName> champ, un <xref:System.UIntPtr?displayProperty=fullName> champ, ou un <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName> champ, mais n’implémente pas <xref:System.IDisposable?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 Cette règle suppose que <xref:System.IntPtr>, <xref:System.UIntPtr>, et <xref:System.Runtime.InteropServices.HandleRef> champs stockent des pointeurs vers des ressources non managées. Les types qui allouent des ressources non managées doivent implémenter <xref:System.IDisposable> pour permettre aux appelants de libérer ces ressources à la demande et de raccourcir les durées de vie des objets qui les détiennent.

 Le modèle de conception recommandée pour nettoyer les ressources non managées consiste à fournir à la fois implicite et un moyen explicite de libérer ces ressources à l’aide de la <xref:System.Object.Finalize%2A?displayProperty=fullName> (méthode) et le <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> (méthode), respectivement. Le garbage collector appelle la <xref:System.Object.Finalize%2A> méthode d’un objet à un moment indéterminé lorsque l’objet est déterminé comme n’étant plus accessible. Après avoir <xref:System.Object.Finalize%2A> est appelée, un autre le garbage collection est nécessaire pour libérer l’objet. Le <xref:System.IDisposable.Dispose%2A> méthode permet à l’appelant de libérer explicitement les ressources à la demande, avant que les ressources sont libérées si le garbage collector. Après avoir nettoyé les ressources non managées, <xref:System.IDisposable.Dispose%2A> doit appeler le <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> méthode pour informer le garbage collector qui <xref:System.Object.Finalize%2A> n’a plus à être appelé ; cela élimine la nécessité pour l’opération garbage collection supplémentaire et raccourcit le durée de vie de l’objet.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, implémentez <xref:System.IDisposable>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si le type ne fait pas référence à une ressource non managée. Sinon, ne supprimez aucun avertissement de cette règle, car échec d’implémentation <xref:System.IDisposable> peut entraîner l’indisponibilité ou la sous-utilisation de ressources non managées.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui implémente <xref:System.IDisposable> pour nettoyer une ressource non managée.

 [!code-csharp[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/CSharp/ca1049-types-that-own-native-resources-should-be-disposable_1.cs)]
 [!code-vb[FxCop.Design.UnmanagedResources#1](../code-quality/codesnippet/VisualBasic/ca1049-types-that-own-native-resources-should-be-disposable_1.vb)]

## <a name="related-rules"></a>Règles associées
 [CA2115 : Appelez GC.KeepAlive lorsque vous utilisez des ressources natives](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)

 [CA1816 : Appelez GC.SuppressFinalize correctement](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)

 [CA2216 : Les types supprimables doivent déclarer un finaliseur](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

 [CA1001 : Les types qui ont des champs supprimables doivent être supprimables](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)

## <a name="see-also"></a>Voir aussi
 [Nettoyer les ressources non managées](/dotnet/standard/garbage-collection/unmanaged) [modèle de suppression](/dotnet/standard/design-guidelines/dispose-pattern)