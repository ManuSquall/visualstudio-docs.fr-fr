---
title: 'CA2115 : Appelez GC.KeepAlive lorsque vous utilisez des ressources natives'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: eb6d28e15870907034479e698ba8e7464f4f5159
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232724"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115 : Appelez GC.KeepAlive lorsque vous utilisez des ressources natives

|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode déclarée dans un type avec un finaliseur référence <xref:System.IntPtr?displayProperty=fullName> un <xref:System.UIntPtr?displayProperty=fullName> champ ou, mais n’appelle <xref:System.GC.KeepAlive%2A?displayProperty=fullName>pas.

## <a name="rule-description"></a>Description de la règle

Le garbage collection finalise un objet s’il n’y a plus de références à celui-ci dans le code managé. Les références non managées aux objets n’empêchent pas garbage collection. Cette règle détecte les erreurs susceptibles de se produire du fait qu’une ressource non managée est en cours de finalisation alors qu’elle est encore utilisée dans un code non managé.

Cette règle suppose que <xref:System.IntPtr> les champs et stockent des pointeurs vers des <xref:System.UIntPtr> ressources non managées. Étant donné que l’objectif d’un finaliseur est de libérer des ressources non managées, la règle part du principe que le finaliseur libérera la ressource non managée vers laquelle pointe les champs de pointeur. Cette règle suppose également que la méthode référence le champ pointeur pour passer la ressource non managée au code non managé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, ajoutez un appel à <xref:System.GC.KeepAlive%2A> à la méthode, en passant l’instance actuelle`this` ( C# dans C++et) comme argument. Positionnez l’appel après la dernière ligne de code où l’objet doit être protégé de garbage collection. Immédiatement après l’appel à <xref:System.GC.KeepAlive%2A>, l’objet est de nouveau considéré comme prêt pour garbage collection en supposant qu’il n’y ait aucune référence managée à ce dernier.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Cette règle effectue quelques hypothèses qui peuvent entraîner des faux positifs. Vous pouvez supprimer sans risque un avertissement de cette règle dans les cas suivants :

- Le finaliseur ne libère pas le contenu du <xref:System.IntPtr> champ ou <xref:System.UIntPtr> référencé par la méthode.

- La méthode ne passe pas le <xref:System.IntPtr> champ <xref:System.UIntPtr> ou au code non managé.

Examinez attentivement les autres messages avant de les exclure. Cette règle détecte les erreurs difficiles à reproduire et à déboguer.

## <a name="example"></a>Exemple

Dans l’exemple suivant, `BadMethod` n’inclut pas d’appel à `GC.KeepAlive` et, par conséquent, viole la règle. `GoodMethod`contient le code corrigé.

> [!NOTE]
> Cet exemple est pseudo-code. Bien que le code se compile et s’exécute, l’avertissement n’est pas déclenché, car une ressource non managée n’est pas créée ou libérée.

[!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.GC.KeepAlive%2A?displayProperty=fullName>
- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.Object.Finalize%2A?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>
- [Dispose, modèle](/dotnet/standard/design-guidelines/dispose-pattern)