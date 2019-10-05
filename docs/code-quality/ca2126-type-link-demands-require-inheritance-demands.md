---
title: "CA2126 : Les demandes de liaison de type exigent des demandes d'héritage"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4f01ba5af7640521333093e4bba1f36a95363b60
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232468"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126 : Les demandes de liaison de type exigent des demandes d'héritage

|||
|-|-|
|TypeName|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Un type non scellé public est protégé par une demande de liaison, a une méthode substituable, et ni le type, ni la méthode n’est protégé par une demande d’héritage.

## <a name="rule-description"></a>Description de la règle
Une demande de liaison sur une méthode ou son type déclarant requiert que l’appelant immédiat de la méthode dispose de l’autorisation spécifiée. Une demande d’héritage sur une méthode nécessite qu’une méthode de substitution ait l’autorisation spécifiée. Une demande d’héritage sur un type nécessite qu’une classe dérivée dispose de l’autorisation spécifiée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, sécurisez le type ou la méthode avec une demande d’héritage pour la même autorisation que la demande de liaison.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
L’exemple suivant montre un type qui viole la règle.

[!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
[!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
[!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>Règles associées
[CA2108 Passer en revue la sécurité déclarative sur les types valeur](../code-quality/ca2108-review-declarative-security-on-value-types.md)

[CA2112 Les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA2122 N’exposez pas indirectement des méthodes avec des demandes de liaison](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

[CA2123 Les demandes de liaison de substitution doivent être identiques à la base](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)
- [Demandes de liaison](/dotnet/framework/misc/link-demands)