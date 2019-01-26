---
title: 'CA2111 : Les pointeurs ne doivent pas être visibles'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 30285ab929cb80e689d70adb267cb17c69a9aff1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55033102"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111 : Les pointeurs ne doivent pas être visibles

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un public ou protégé <xref:System.IntPtr?displayProperty=fullName> ou <xref:System.UIntPtr?displayProperty=fullName> champ n’est pas en lecture seule.

## <a name="rule-description"></a>Description de la règle
 <xref:System.IntPtr> et <xref:System.UIntPtr> sont des types de pointeur qui servent à accéder à la mémoire non managée. Si un pointeur n’est pas privée, interne ou en lecture seule, un code malveillant peut modifier la valeur du pointeur, potentiellement autorisant l’accès aux emplacements arbitraires en mémoire ou provoquant des défaillances des applications ou du système.

 Si vous avez l’intention pour sécuriser l’accès au type qui contient le champ de pointeur, consultez [CA2112 : Types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Sécurisez le pointeur en le rendant en lecture seule, interne ou privé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle si vous ne comptez pas sur la valeur du pointeur.

## <a name="example"></a>Exemple
 Le code suivant montre des pointeurs qui violent et satisfaire à la règle. Notez que les pointeurs non privés violent également la règle [CA1051 : Ne déclarez pas de champs d’instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../code-quality/codesnippet/CSharp/ca2111-pointers-should-not-be-visible_1.cs)]

## <a name="related-rules"></a>Règles associées
 [CA2112 : Types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051 : Ne déclarez pas de champs d’instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.IntPtr?displayProperty=fullName>
- <xref:System.UIntPtr?displayProperty=fullName>