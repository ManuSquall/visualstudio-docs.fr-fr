---
title: 'CA2116 : Les méthodes APTCA doivent uniquement appeler des méthodes APTCA'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 6ecd6c5a51feb025eb5e90fa63ae0b2a8bf877ed
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029789"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116 : Les méthodes APTCA doivent uniquement appeler des méthodes APTCA

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Une méthode dans un assembly avec le <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> attribut appelle une méthode dans un assembly qui n’a pas l’attribut.

## <a name="rule-description"></a>Description de la règle

Par défaut, les méthodes publiques ou protégées dans les assemblys avec noms forts sont implicitement protégés par un [demandes de liaison](/dotnet/framework/misc/link-demands) de confiance totale ; uniquement de confiance suffisant pour les appelants peuvent accéder à un assembly avec nom fort. Assemblys avec nom fort est marqué avec le <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribut (APTCA) n’ont pas cette protection. L’attribut désactive la demande de liaison, ce qui rend l’assembly accessible aux appelants qui n’ont pas de confiance totale, comme le code exécuté à partir d’un intranet ou Internet.

Lorsque l’attribut APTCA est présent sur un assembly entièrement fiable, et l’assembly exécute le code dans un autre assembly qui n’autorise pas les appelants partiellement approuvés, une faille de sécurité est possible. Si deux méthodes `M1` et `M2` remplir les conditions suivantes, des appelants malveillants peuvent utiliser la méthode `M1` pour ignorer la demande de liaison de confiance totale implicite qui protège `M2`:

- `M1` une méthode publique est déclarée dans un assembly entièrement fiable qui possède l’attribut APTCA.

- `M1` appelle une méthode `M2` en dehors de `M1`d’assembly.

- `M2`d’assembly n’a pas l’attribut APTCA et, par conséquent, ne doit pas être exécuté par ou pour le compte des appelants partiellement approuvés.

Un appelant de confiance partiel `X` peut appeler méthode `M1`, ce qui provoque `M1` pour appeler `M2`. Étant donné que `M2` n’a pas l’attribut APTCA, son appelant immédiat (`M1`) doit satisfaire une demande de liaison pour la confiance totale ; `M1` dispose d’une confiance totale et par conséquent satisfait cette vérification. Le risque de sécurité est car `X` ne contribue pas à satisfaire la demande de liaison qui protège `M2` provenant d’appelants non approuvés. Par conséquent, les méthodes avec l’attribut APTCA ne doivent pas appeler les méthodes qui n’ont pas l’attribut.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Si l’attribut APCTA est requis, utilisez une demande pour protéger la méthode qui appelle l’assembly de confiance totale. Les autorisations exactes à la demande vous dépend de la fonctionnalité exposée par votre méthode. S’il est possible, protégez la méthode avec une demande de confiance totale pour s’assurer que la fonctionnalité sous-jacente n’est pas exposée aux appelants partiellement approuvés. Si ce n’est pas possible, sélectionnez un jeu d’autorisations qui protègent efficacement les fonctionnalités exposées.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que la fonctionnalité exposée par votre méthode de ne pas, directement ou indirectement, permet aux appelants d’accéder aux informations sensibles, des opérations ou des ressources qui peuvent être utilisées dans une action destructrice.

## <a name="example-1"></a>Exemple 1
 L’exemple suivant utilise deux assemblys et une application de test pour illustrer la vulnérabilité de sécurité détectée par cette règle. Le premier assembly n’a pas l’attribut APTCA et ne doit pas être accessible aux appelants partiellement approuvés (représenté par `M2` dans la discussion précédente).

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example-2"></a>Exemple 2
 Le deuxième assembly est entièrement fiable et permet aux appelants de confiance partielle (représenté par `M1` dans la discussion précédente).

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example-3"></a>Exemple 3
 L’application de test (représentée par `X` dans la discussion précédente) est partiellement approuvé.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

Cet exemple génère la sortie suivante :

```txt
Demand for full trust:Request failed.
ClassRequiringFullTrust.DoWork was called.
```

## <a name="related-rules"></a>Règles associées

- [CA2117 : Les types APTCA doivent uniquement étendre des types de base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)
- [Utilisation de bibliothèques à partir de code d’un niveau de confiance partiel](/dotnet/framework/misc/using-libraries-from-partially-trusted-code)
- [Demandes de liaison](/dotnet/framework/misc/link-demands)
- [Données et modélisation](/dotnet/framework/data/index)