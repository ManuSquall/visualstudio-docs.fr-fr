---
title: 'CA2108 : Vérifiez la sécurité déclarative dans les types valeur'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c62704a99e5952c313c4ba11a71fd234070d6df8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882232"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108 : Vérifiez la sécurité déclarative dans les types valeur

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un type valeur public ou protégé est sécurisé par un [données et modélisation](/dotnet/framework/data/index) ou [demandes de liaison](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Description de la règle

Les types valeur sont alloués et initialisés par leurs constructeurs par défaut avant d’exécutent d’autres constructeurs. Si un type valeur est sécurisé par un LinkDemand ou un à la demande, et l’appelant n’a pas d’autorisations qui répondent à la vérification de sécurité, un constructeur autre que la valeur par défaut échoue, et une exception de sécurité est levée. Le type de valeur n’est pas libéré ; Il reste dans l’état défini par son constructeur par défaut. Ne supposez pas que l’appelant qui passe une instance du type valeur est autorisé à créer ou accéder à l’instance.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Vous ne pouvez pas corriger une violation de cette règle, sauf si vous supprimez la vérification de sécurité du type, et utiliser la sécurité au niveau méthode vérifie à la place. Correction de la violation de cette manière n’empêche pas les appelants dotés d’autorisations inadéquates d’obtenir des instances du type valeur. Vous devez vous assurer qu’une instance du type valeur, dans son état par défaut, n’expose pas d’informations sensibles et ne peut pas être utilisée de façon préjudiciable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Vous pouvez supprimer un avertissement de cette règle si un appelant peut obtenir des instances du type valeur dans son état par défaut sans que cela constitue une menace pour la sécurité.

## <a name="example-1"></a>Exemple 1

L’exemple suivant montre une bibliothèque contenant un type valeur qui enfreint cette règle. Le `StructureManager` type suppose qu’un appelant qui passe une instance du type valeur est autorisé à créer ou accéder à l’instance.

[!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]

## <a name="example-2"></a>Exemple 2

L’application suivante montre la faiblesse de la bibliothèque.

[!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]

Cet exemple génère la sortie suivante :

```txt
Structure custom constructor: Request failed.
New values SecuredTypeStructure 100 100
New values SecuredTypeStructure 200 200
```

## <a name="see-also"></a>Voir aussi

- [Demandes de liaison](/dotnet/framework/misc/link-demands)
- [Données et modélisation](/dotnet/framework/data/index)
