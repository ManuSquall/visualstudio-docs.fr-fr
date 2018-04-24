---
title: 'CA2116 : Les méthodes APTCA doivent uniquement appeler des méthodes APTCA'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 300b08d6fd00a9bf2a38e738a3b4d433111cb8c7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
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
 Par défaut, les méthodes publiques ou protégées dans les assemblys avec noms forts sont protégées implicitement par un [les demandes de liaison](/dotnet/framework/misc/link-demands) pour la confiance totale ; uniquement entièrement fiables appelants puissent accéder à un assembly avec nom fort. Assemblys avec nom fort est marqué avec le <xref:System.Security.AllowPartiallyTrustedCallersAttribute> de l’attribut (APTCA) n’ont pas cette protection. L’attribut désactive la demande de liaison, rendant l’assembly accessible aux appelants qui n’ont pas d’une confiance totale, tel que le code de l’exécution à partir d’un intranet ou Internet.

 Lorsque l’attribut APTCA est présent sur un assembly entièrement fiable, et l’assembly exécute un code dans un autre assembly qui n’autorise pas les appelants partiellement approuvés, une attaque de sécurité est possible. Si deux méthodes `M1` et `M2` remplissent les conditions suivantes, des appelants malveillants peuvent utiliser la méthode `M1` pour ignorer la demande de liaison de confiance totale implicite qui protège `M2`:

-   `M1` une méthode publique est déclarée dans un assembly entièrement fiable qui possède l’attribut APTCA.

-   `M1` appelle une méthode `M2` en dehors de `M1`d’assembly.

-   `M2`d’assembly n’a pas l’attribut APTCA et, par conséquent, ne doit pas être exécuté par ou pour le compte des appelants partiellement approuvés.

 Un niveau de confiance partielle appelant `X` pouvez appeler la méthode `M1`, ce qui provoque `M1` pour appeler `M2`. Étant donné que `M2` n’a pas l’attribut APTCA, son appelant immédiat (`M1`) doit satisfaire une demande de liaison pour la confiance totale ; `M1` dispose d’une confiance totale et par conséquent satisfait cette vérification. Le risque de sécurité est car `X` ne participe pas satisfaire la demande de liaison qui protège `M2` provenant d’appelants non fiables. Par conséquent, les méthodes avec l’attribut APTCA ne doivent pas appeler les méthodes qui n’ont pas l’attribut.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Si l’attribut APCTA est requis, utilisez une demande pour protéger la méthode qui appelle l’assembly de confiance totale. Les autorisations exactes que vous la demande dépend de la fonctionnalité exposée par votre méthode. S’il est possible, protégez la méthode avec une demande pour une confiance totale pour s’assurer que la fonctionnalité sous-jacente n’est pas exposée aux appelants partiellement approuvés. Si ce n’est pas possible, sélectionnez un jeu d’autorisations qui protègent efficacement les fonctionnalités exposées.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que la fonctionnalité exposée par votre méthode pas directement ou indirectement autorise les appelants d’accéder aux informations sensibles, des opérations ou des ressources qui peuvent être utilisées dans une action destructrice.

## <a name="example"></a>Exemple
 L’exemple suivant utilise deux assemblys et une application de test pour illustrer la vulnérabilité de sécurité détectée par cette règle. Le premier assembly ne dispose pas de l’attribut APTCA et ne doit pas être accessible aux appelants partiellement approuvés (représenté par `M2` dans la discussion précédente).

 [!code-csharp[FxCop.Security.NoAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_1.cs)]

## <a name="example"></a>Exemple
 Le deuxième assembly est entièrement fiable et autorise les appelants partiellement approuvés (représenté par `M1` dans la discussion précédente).

 [!code-csharp[FxCop.Security.YesAptca#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_2.cs)]

## <a name="example"></a>Exemple
 L’application de test (représentée par `X` dans la discussion précédente) est le niveau de confiance partiel.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../code-quality/codesnippet/CSharp/ca2116-aptca-methods-should-only-call-aptca-methods_3.cs)]

 Cet exemple produit la sortie suivante.

 **Échec de la demande d’approbation : demande complète. ** 
 **ClassRequiringFullTrust.DoWork a été appelé.**
## <a name="related-rules"></a>Règles associées
 [CA2117 : Les types APTCA doivent étendre seulement des types de base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Voir aussi
 [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines) [partiellement à l’aide de bibliothèques à partir d’un Code de confiance](/dotnet/framework/misc/using-libraries-from-partially-trusted-code) [demandes de liaison](/dotnet/framework/misc/link-demands) [données et modélisation](/dotnet/framework/data/index)