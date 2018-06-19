---
title: 'CA2115 : Appelez GC.KeepAlive lorsque vous utilisez des ressources natives'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 66621bec3316dfcee92a1e5b1d1d1a8d97ae5c54
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914651"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115 : Appelez GC.KeepAlive lorsque vous utilisez des ressources natives
|||
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode déclarée dans un type avec un finaliseur fait référence à un <xref:System.IntPtr?displayProperty=fullName> ou <xref:System.UIntPtr?displayProperty=fullName> champ, mais n’appelle pas <xref:System.GC.KeepAlive%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 Le garbage collection finalise un objet s’il en existe aucune plus référence à celle-ci dans le code managé. Des références non managées à des objets n’empêchent pas le garbage collection. Cette règle détecte les erreurs susceptibles de se produire du fait qu'une ressource non managée est en cours de finalisation alors qu'elle est encore utilisée dans un code non managé.

 Cette règle suppose que <xref:System.IntPtr> et <xref:System.UIntPtr> champs stockent des pointeurs vers des ressources non managées. Étant donné que l’objectif d’un finaliseur est de libérer des ressources non managées, la règle suppose que le finaliseur libère la ressource non managée vers laquelle pointée les champs de pointeur. Cette règle suppose également que la méthode référence le champ de pointeur pour passer la ressource non managée au code non managé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez un appel à <xref:System.GC.KeepAlive%2A> à la méthode, en passant l’instance actuelle (`this` en c# et C++) comme argument. Placez l’appel après la dernière ligne de code où l’objet doit être protégé contre le garbage collection. Immédiatement après l’appel à <xref:System.GC.KeepAlive%2A>, l’objet est à nouveau considéré comme prêt pour le garbage collection en supposant qu’il n’existe aucune référence managée.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Cette règle émet des hypothèses pouvant conduire à des faux positifs. Vous pouvez supprimer sans risque un avertissement de cette règle si :

-   Le finaliseur ne libère pas le contenu de la <xref:System.IntPtr> ou <xref:System.UIntPtr> champ référencé par la méthode.

-   La méthode ne passe pas le <xref:System.IntPtr> ou <xref:System.UIntPtr> champ au code non managé.

 Lisez attentivement les autres messages avant de les exclure. Cette règle détecte les erreurs qui sont difficiles à reproduire et à déboguer.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, `BadMethod` n’inclut pas d’un appel à `GC.KeepAlive` et par conséquent ne respecte pas la règle. `GoodMethod` contient le code corrigé.

> [!NOTE]
>  Cet exemple est pseudo-code, bien que le code est compilé et exécuté, l’avertissement n’est pas déclenché parce qu’une ressource non managée n’est pas créée ou libérée.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../code-quality/codesnippet/CSharp/ca2115-call-gc-keepalive-when-using-native-resources_1.cs)]

## <a name="see-also"></a>Voir aussi
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName> <xref:System.Object.Finalize%2A?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName> [Modèle de suppression](/dotnet/standard/design-guidelines/dispose-pattern)