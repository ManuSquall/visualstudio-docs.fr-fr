---
title: 'CA2112 : Les types sécurisés ne doivent pas exposer de champs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48cfcfd4feb794137e1634158b5af632aa976c60
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232763"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112 : Les types sécurisés ne doivent pas exposer de champs

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Un type public ou protégé contient des champs publics et est sécurisé par une [demande de liaison](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Description de la règle
Si un code a accès à une instance d’un type sécurisé par une demande de liaison, ce code n’a pas besoin de satisfaire la demande de liaison pour accéder aux champs du type.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, rendez les champs non publics et ajoutez des propriétés ou des méthodes publiques qui retournent les données de champ. Les vérifications de sécurité LinkDemand sur les types protègent l’accès aux propriétés et méthodes du type. Toutefois, la sécurité d’accès du code ne s’applique pas aux champs.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Pour les problèmes de sécurité et pour une bonne conception, vous devez corriger les violations en rendant les champs publics non publics. Vous pouvez supprimer un avertissement de cette règle si le champ ne contient pas d’informations qui doivent rester sécurisées et que vous ne vous fiez pas au contenu du champ.

## <a name="example"></a>Exemple
L’exemple suivant est composé d’un type de bibliothèque`SecuredTypeWithFields`() avec des champs non sécurisés, d'`Distributor`un type () qui peut créer des instances du type de bibliothèque et de passe des instances à des types ne sont pas autorisés à les créer, et le code d’application qui peut lire les champs d’une instance, même s’il n’a pas l’autorisation qui sécurise le type.

Le code de bibliothèque suivant enfreint la règle.

[!code-csharp[FxCop.Security.LinkDemandOnField#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_1.cs)]

## <a name="example-1"></a>Exemple 1
L’application ne peut pas créer d’instance en raison de la demande de liaison qui protège le type sécurisé. La classe suivante permet à l’application d’obtenir une instance du type sécurisé.

[!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_2.cs)]

## <a name="example-2"></a>Exemple 2
L’application suivante illustre comment, sans l’autorisation d’accéder aux méthodes d’un type sécurisé, le code peut accéder à ses champs.

[!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../code-quality/codesnippet/CSharp/ca2112-secured-types-should-not-expose-fields_3.cs)]

Cet exemple génère la sortie suivante :

```txt
Creating an instance of SecuredTypeWithFields.
Secured type fields: 22, 33
Changing secured type's field...
Cached Object fields: 99, 33
```

## <a name="related-rules"></a>Règles associées

- [CA1051 Ne pas déclarer les champs d’instance visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>Voir aussi

- [Demandes de liaison](/dotnet/framework/misc/link-demands)
- [Données et modélisation](/dotnet/framework/data/index)