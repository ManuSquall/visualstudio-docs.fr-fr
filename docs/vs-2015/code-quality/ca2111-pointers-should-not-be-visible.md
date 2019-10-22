---
title: 'CA2111 : les pointeurs ne doivent pas être visibles | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PointersShouldNotBeVisible
- CA2111
helpviewer_keywords:
- CA2111
- PointersShouldNotBeVisible
ms.assetid: b3a8d466-895b-43bc-a2df-5d7058fe915f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a0d5546c6f6a2f5dbd0c6063f4a1dfd40ce1d7bb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658737"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111 : Les pointeurs ne doivent pas être visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PointersShouldNotBeVisible|
|CheckId|CA2111|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un champ public ou protégé <xref:System.IntPtr?displayProperty=fullName> ou <xref:System.UIntPtr?displayProperty=fullName> n’est pas en lecture seule.

## <a name="rule-description"></a>Description de la règle
 <xref:System.IntPtr> et <xref:System.UIntPtr> sont des types pointeur utilisés pour accéder à la mémoire non managée. Si un pointeur n’est pas privé, interne ou en lecture seule, un code malveillant peut modifier la valeur du pointeur, autorisant potentiellement l’accès à des emplacements arbitraires en mémoire ou provoquant des défaillances de l’application ou du système.

 Si vous envisagez de sécuriser l’accès au type qui contient le champ pointeur, consultez [CA2112 : les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Sécurisez le pointeur en le rendant accessible en lecture seule, interne ou privé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle si vous ne vous fiez pas à la valeur du pointeur.

## <a name="example"></a>Exemple
 Le code suivant affiche des pointeurs qui violent et satisfont la règle. Notez que les pointeurs non privés violent également la règle [CA1051 : ne déclarez pas les champs d’instance visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA2112 : Les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051 : Ne déclarez pas de champs d’instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>
