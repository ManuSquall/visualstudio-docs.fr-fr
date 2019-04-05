---
title: 'CA2111 : Les pointeurs ne doivent pas être visibles | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8497433088e4c49868a76dd3281d02a5e79babe5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952960"
---
# <a name="ca2111-pointers-should-not-be-visible"></a>CA2111 : Les pointeurs ne doivent pas être visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-csharp[FxCop.Security.PointersArePrivate#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.PointersArePrivate/cs/FxCop.Security.PointersArePrivate.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA2112 : Types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

 [CA1051 : Ne déclarez pas de champs d’instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.IntPtr?displayProperty=fullName> <xref:System.UIntPtr?displayProperty=fullName>
