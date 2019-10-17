---
title: 'CA1001 : Les types qui possèdent des champs supprimables doivent être supprimables'
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
ms.openlocfilehash: f49624e4e39bb0b3c1a0c1be7f32e797536d30eb
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72431794"
---
# <a name="ca1001-types-that-own-disposable-fields-should-be-disposable"></a>CA1001 : Les types qui possèdent des champs supprimables doivent être supprimables

|||
|-|-|
|TypeName|TypesThatOwnDisposableFieldsShouldBeDisposable|
|CheckId|CA1001|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture : si le type n’est pas visible à l’extérieur de l’assembly.<br /><br /> Avec rupture : si le type est visible à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause
Une classe déclare et implémente un champ d’instance qui est un type <xref:System.IDisposable?displayProperty=fullName> et la classe n’implémente pas <xref:System.IDisposable>.

## <a name="rule-description"></a>Description de la règle
Une classe implémente l’interface <xref:System.IDisposable> pour supprimer les ressources non managées qu’elle possède. Un champ d’instance qui est un type <xref:System.IDisposable> indique que le champ est propriétaire d’une ressource non managée. Une classe qui déclare un champ <xref:System.IDisposable> possède indirectement une ressource non managée et doit implémenter l’interface <xref:System.IDisposable>. Si la classe ne possède pas directement de ressources non managées, elle ne doit pas implémenter de finaliseur.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, implémentez <xref:System.IDisposable> et à partir de la méthode <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> appellent la méthode <xref:System.IDisposable.Dispose%2A> du champ.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
L’exemple suivant montre une classe qui enfreint la règle et une classe qui satisfait la règle en implémentant <xref:System.IDisposable>. La classe n’implémente pas de finaliseur, car la classe ne possède pas directement de ressources non managées.

[!code-vb[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/VisualBasic/ca1001-types-that-own-disposable-fields-should-be-disposable_1.vb)]
[!code-csharp[FxCop.Design.DisposableFields#1](../code-quality/codesnippet/CSharp/ca1001-types-that-own-disposable-fields-should-be-disposable_1.cs)]

## <a name="related-rules"></a>Règles associées
[CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213.md)

[CA2216 : Les types supprimables doivent déclarer un finaliseur](../code-quality/ca2216.md)

[CA2215 : Les méthodes Dispose doivent appeler la méthode Dispose de la classe de base](../code-quality/ca2215.md)

[CA1049 : Les types qui ont des ressources natives doivent être supprimables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)
