---
title: 'CA2116 : Les méthodes APTCA doivent uniquement appeler des méthodes APTCA'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f09817e9248fdc28f56ac0162e783bf72643ee5c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232685"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116 : Les méthodes APTCA doivent uniquement appeler des méthodes APTCA

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Une méthode dans un assembly avec <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> l’attribut appelle une méthode dans un assembly qui n’a pas l’attribut.

## <a name="rule-description"></a>Description de la règle

Par défaut, les méthodes publiques ou protégées des assemblys avec des noms forts sont protégées implicitement par une [demande de liaison](/dotnet/framework/misc/link-demands) pour une confiance totale. Seuls les appelants d’un niveau de confiance suffisant peuvent accéder à un assembly avec nom fort. Les assemblys avec nom fort marqués avec <xref:System.Security.AllowPartiallyTrustedCallersAttribute> l’attribut (APTCA) n’ont pas cette protection. L’attribut désactive la demande de liaison, ce qui rend l’assembly accessible aux appelants qui ne bénéficient pas d’une confiance totale, tels que le code qui s’exécute à partir d’un intranet ou d’Internet.

Lorsque l’attribut APTCA est présent dans un assembly entièrement fiable et que l’assembly exécute du code dans un autre assembly qui n’autorise pas les appelants d’un niveau de confiance partiel, une faille de sécurité est possible. Si deux méthodes `M1` et `M2` remplissent les conditions suivantes, les appelants malveillants peuvent `M1` utiliser la méthode pour contourner la demande de liaison `M2`de confiance totale implicite qui protège :

- `M1`est une méthode publique déclarée dans un assembly de confiance totale qui a l’attribut APTCA.

- `M1`appelle une méthode `M2` à `M1`l’extérieur de l’assembly.

- `M2`l’assembly de n’a pas l’attribut APTCA et, par conséquent, ne doit pas être exécuté par ou pour le compte des appelants qui ont un niveau de confiance partiel.

Un appelant `X` de confiance partielle peut appeler `M1`la méthode `M1` , provoquant l’appel `M2`à. Étant `M2` donné que n’a pas l’attribut APTCA, son appelant`M1`immédiat () doit satisfaire une demande de liaison pour une confiance totale. `M1` dispose d’une confiance totale et, par conséquent, est conforme à cette vérification. Le risque de sécurité est `X` que ne participe pas à la satisfaction de la demande `M2` de liaison qui protège contre les appelants non fiables. Par conséquent, les méthodes avec l’attribut APTCA ne doivent pas appeler de méthodes qui n’ont pas l’attribut.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Si l’attribut APCTA est requis, utilisez une demande pour protéger la méthode qui appelle l’assembly de confiance totale. Les autorisations exactes que vous demandez dépendent de la fonctionnalité exposée par votre méthode. Si possible, Protégez la méthode avec une demande de confiance totale pour garantir que la fonctionnalité sous-jacente n’est pas exposée aux appelants d’un niveau de confiance partiel. Si ce n’est pas possible, sélectionnez un ensemble d’autorisations qui protègent efficacement les fonctionnalités exposées.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que la fonctionnalité exposée par votre méthode ne permet pas directement ou indirectement aux appelants d’accéder à des informations sensibles, à des opérations ou à des ressources qui peuvent être utilisées de manière destructrice.

## <a name="example-1"></a>Exemple 1
L’exemple suivant utilise deux assemblys et une application de test pour illustrer la vulnérabilité de sécurité détectée par cette règle. Le premier assembly n’a pas l’attribut APTCA et ne doit pas être accessible aux appelants de confiance partielle `M2` (représenté par dans la discussion précédente).

[!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example-2"></a>Exemple 2
Le deuxième assembly est entièrement fiable et autorise les appelants partiellement approuvés ( `M1` représenté par dans la discussion précédente).

[!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example-3"></a>Exemple 3
L’application de test (représentée `X` par dans la discussion précédente) est de confiance partielle.

[!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

Cet exemple génère la sortie suivante :

```txt
Demand for full trust:Request failed.
ClassRequiringFullTrust.DoWork was called.
```

## <a name="related-rules"></a>Règles associées

- [CA2117 Les types APTCA doivent uniquement étendre les types de base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)
- [Utilisation de bibliothèques à partir de code d’un niveau de confiance partiel](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
- [Demandes de liaison](/dotnet/framework/misc/link-demands)
- [Données et modélisation](/dotnet/framework/data/index)