---
title: 'CA2115 : appelez GC. KeepAlive quand vous utilisez des ressources natives | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGCKeepAliveWhenUsingNativeResources
- CA2115
helpviewer_keywords:
- CA2115
- CallGCKeepAliveWhenUsingNativeResources
ms.assetid: f00a59a7-2c6a-4bbe-a1b3-7bf77d366f34
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c668172ca318000068fb4e90f4848e456c32208d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543622"
---
# <a name="ca2115-call-gckeepalive-when-using-native-resources"></a>CA2115 : Appelez GC.KeepAlive lorsque vous utilisez des ressources natives
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|CallGCKeepAliveWhenUsingNativeResources|
|CheckId|CA2115|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode déclarée dans un type avec un finaliseur référence <xref:System.IntPtr?displayProperty=fullName> un <xref:System.UIntPtr?displayProperty=fullName> champ ou, mais n’appelle pas <xref:System.GC.KeepAlive%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Description de la règle
 Le garbage collection finalise un objet s’il n’y a plus de références à celui-ci dans le code managé. Les références non managées aux objets n’empêchent pas garbage collection. Cette règle détecte les erreurs susceptibles de se produire du fait qu’une ressource non managée est en cours de finalisation alors qu’elle est encore utilisée dans un code non managé.

 Cette règle suppose que <xref:System.IntPtr> les <xref:System.UIntPtr> champs et stockent des pointeurs vers des ressources non managées. Étant donné que l’objectif d’un finaliseur est de libérer des ressources non managées, la règle part du principe que le finaliseur libérera la ressource non managée vers laquelle pointe les champs de pointeur. Cette règle suppose également que la méthode référence le champ pointeur pour passer la ressource non managée au code non managé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez un appel à <xref:System.GC.KeepAlive%2A> la méthode, en passant l’instance actuelle ( `this` en C# et C++) comme argument. Positionnez l’appel après la dernière ligne de code où l’objet doit être protégé de garbage collection. Immédiatement après l’appel à <xref:System.GC.KeepAlive%2A> , l’objet est de nouveau considéré comme prêt pour garbage collection en supposant qu’il n’y ait aucune référence managée à ce dernier.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Cette règle effectue quelques hypothèses qui peuvent entraîner des faux positifs. Vous pouvez supprimer sans risque un avertissement de cette règle dans les cas suivants :

- Le finaliseur ne libère pas le contenu du <xref:System.IntPtr> champ ou <xref:System.UIntPtr> référencé par la méthode.

- La méthode ne passe pas le <xref:System.IntPtr> <xref:System.UIntPtr> champ ou au code non managé.

  Examinez attentivement les autres messages avant de les exclure. Cette règle détecte les erreurs difficiles à reproduire et à déboguer.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, `BadMethod` n’inclut pas d’appel à `GC.KeepAlive` et, par conséquent, viole la règle. `GoodMethod`contient le code corrigé.

> [!NOTE]
> Cet exemple est pseudo-code même si le code est compilé et exécuté, l’avertissement n’est pas déclenché, car une ressource non managée n’est pas créée ou libérée.

 [!code-csharp[FxCop.Security.IntptrAndFinalize#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.IntptrAndFinalize/cs/FxCop.Security.IntptrAndFinalize.cs#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> <xref:System.IntPtr?displayProperty=fullName>
 <xref:System.Object.Finalize%2A?displayProperty=fullName>
 <xref:System.UIntPtr?displayProperty=fullName>
 [Dispose, modèle](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
