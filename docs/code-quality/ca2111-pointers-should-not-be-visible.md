---
title: 'CA2111 : Les pointeurs ne doivent pas être visibles'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a93f776ac6e133b0ebf79d1dfa56f802ff66e5f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232781"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111 : Les pointeurs ne doivent pas être visibles

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Un champ public ou <xref:System.IntPtr?displayProperty=fullName> protégé <xref:System.UIntPtr?displayProperty=fullName> ou n’est pas en lecture seule.

## <a name="rule-description"></a>Description de la règle
 <xref:System.IntPtr>et <xref:System.UIntPtr> sont des types pointeur utilisés pour accéder à la mémoire non managée. Si un pointeur n’est pas privé, interne ou en lecture seule, un code malveillant peut modifier la valeur du pointeur, autorisant potentiellement l’accès à des emplacements arbitraires en mémoire ou provoquant des défaillances de l’application ou du système.

Si vous envisagez de sécuriser l’accès au type qui contient le champ [pointeur, consultez CA2112 : Les types sécurisés ne doivent](../code-quality/ca2112-secured-types-should-not-expose-fields.md)pas exposer de champs.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Sécurisez le pointeur en le rendant accessible en lecture seule, interne ou privé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Supprimez un avertissement de cette règle si vous ne vous fiez pas à la valeur du pointeur.

## <a name="example"></a>Exemple
Le code suivant affiche des pointeurs qui violent et satisfont la règle. Notez que les pointeurs non privés violent également la règle [CA1051 : Ne déclarez pas les champs](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)d’instance visibles.

[!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>Règles associées
[CA2112 Les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA1051 Ne pas déclarer les champs d’instance visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>