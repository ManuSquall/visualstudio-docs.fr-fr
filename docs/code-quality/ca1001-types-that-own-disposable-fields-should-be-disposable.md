---
title: 'CA1001 : Les types qui possèdent des champs supprimables doivent être supprimables'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
helpviewer_keywords:
- CA1001
- TypesThatOwnDisposableFieldsShouldBeDisposable
ms.assetid: c85c126c-2b16-4505-940a-b5ddf873fb22
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3bda8fc80992a2246c30e28582eb93b4624ab81c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236691"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001 : Les types qui possèdent des champs supprimables doivent être supprimables

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture : si le type n’est pas visible à l’extérieur de l’assembly.<br /><br /> Avec rupture : si le type est visible à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause
Une classe déclare et implémente un champ d’instance qui est un <xref:System.IDisposable?displayProperty=fullName> type et la classe n’implémente <xref:System.IDisposable>pas.

## <a name="rule-description"></a>Description de la règle
Une classe implémente l' <xref:System.IDisposable> interface pour supprimer les ressources non managées qu’elle possède. Un champ d’instance qui est <xref:System.IDisposable> un type indique que le champ est propriétaire d’une ressource non managée. Une classe qui déclare un <xref:System.IDisposable> champ possède indirectement une ressource non managée et doit implémenter l' <xref:System.IDisposable> interface. Si la classe ne possède pas directement de ressources non managées, elle ne doit pas implémenter de finaliseur.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, implémentez <xref:System.IDisposable> et à partir de la <xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> méthode appelez la méthode du champ.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
L’exemple suivant montre une classe qui enfreint la règle et une classe qui satisfait la règle en implémentant <xref:System.IDisposable>. La classe n’implémente pas de finaliseur, car la classe ne possède pas directement de ressources non managées.

[!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
[!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Règles associées
[CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

[CA2216 Les types jetables doivent déclarer un finaliseur](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

[CA2215 Les méthodes dispose doivent appeler la méthode dispose de la classe de base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

[CA1049 Les types qui possèdent des ressources natives doivent être supprimables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)