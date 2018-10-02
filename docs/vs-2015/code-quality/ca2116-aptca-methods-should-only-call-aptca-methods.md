---
title: 'CA2116 : Les méthodes APTCA doivent uniquement appeler des méthodes APTCA | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 78e3136ed2671de2962ae4de994bae178fcbceca
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589698"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116 : Les méthodes APTCA doivent uniquement appeler des méthodes APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2116 : les méthodes APTCA doivent uniquement appeler des méthodes APTCA](https://docs.microsoft.com/visualstudio/code-quality/ca2116-aptca-methods-should-only-call-aptca-methods).

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode dans un assembly avec le <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> attribut appelle une méthode dans un assembly qui n’a pas l’attribut.

## <a name="rule-description"></a>Description de la règle
 Par défaut, les méthodes publiques ou protégées dans les assemblys avec noms forts sont implicitement protégés par un [demandes de liaison](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) de confiance totale ; uniquement de confiance suffisant pour les appelants peuvent accéder à un assembly avec nom fort. Assemblys avec nom fort est marqué avec le <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribut (APTCA) n’ont pas cette protection. L’attribut désactive la demande de liaison, ce qui rend l’assembly accessible aux appelants qui n’ont pas de confiance totale, comme le code exécuté à partir d’un intranet ou Internet.

 Lorsque l’attribut APTCA est présent sur un assembly entièrement fiable, et l’assembly exécute le code dans un autre assembly qui n’autorise pas les appelants partiellement approuvés, une faille de sécurité est possible. Si deux méthodes `M1` et `M2` remplir les conditions suivantes, des appelants malveillants peuvent utiliser la méthode `M1` pour ignorer la demande de liaison de confiance totale implicite qui protège `M2`:

-   `M1` une méthode publique est déclarée dans un assembly entièrement fiable qui possède l’attribut APTCA.

-   `M1` appelle une méthode `M2` en dehors de `M1`d’assembly.

-   `M2`d’assembly n’a pas l’attribut APTCA et, par conséquent, ne doit pas être exécuté par ou pour le compte des appelants partiellement approuvés.

 Un appelant de confiance partiel `X` peut appeler méthode `M1`, ce qui provoque `M1` pour appeler `M2`. Étant donné que `M2` n’a pas l’attribut APTCA, son appelant immédiat (`M1`) doit satisfaire une demande de liaison pour la confiance totale ; `M1` dispose d’une confiance totale et par conséquent satisfait cette vérification. Le risque de sécurité est car `X` ne contribue pas à satisfaire la demande de liaison qui protège `M2` provenant d’appelants non approuvés. Par conséquent, les méthodes avec l’attribut APTCA ne doivent pas appeler les méthodes qui n’ont pas l’attribut.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Si l’attribut APCTA est requis, utilisez une demande pour protéger la méthode qui appelle l’assembly de confiance totale. Les autorisations exactes à la demande vous dépend de la fonctionnalité exposée par votre méthode. S’il est possible, protégez la méthode avec une demande de confiance totale pour s’assurer que la fonctionnalité sous-jacente n’est pas exposée aux appelants partiellement approuvés. Si ce n’est pas possible, sélectionnez un jeu d’autorisations qui protègent efficacement les fonctionnalités exposées. Pour plus d’informations sur les demandes, consultez [demandes](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que la fonctionnalité exposée par votre méthode de ne pas, directement ou indirectement, permet aux appelants d’accéder aux informations sensibles, des opérations ou des ressources qui peuvent être utilisées dans une action destructrice.

## <a name="example"></a>Exemple
 L’exemple suivant utilise deux assemblys et une application de test pour illustrer la vulnérabilité de sécurité détectée par cette règle. Le premier assembly n’a pas l’attribut APTCA et ne doit pas être accessible aux appelants partiellement approuvés (représenté par `M2` dans la discussion précédente).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Exemple
 Le deuxième assembly est entièrement fiable et permet aux appelants de confiance partielle (représenté par `M1` dans la discussion précédente).

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Exemple
 L’application de test (représentée par `X` dans la discussion précédente) est partiellement approuvé.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 Cet exemple produit la sortie suivante.

 **Échec de la demande d’approbation : demande complète. ** 
 **ClassRequiringFullTrust.DoWork a été appelé.**
## <a name="related-rules"></a>Règles associées
 [CA2117 : Les types APTCA doivent étendre seulement des types de base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Voir aussi
 [Instructions de codage sécurisé](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [assemblys .NET Framework peut être appelés par le Code partiellement fiable](http://msdn.microsoft.com/en-us/a417fcd4-d3ca-4884-a308-3a1a080eac8d) [partiellement à l’aide de bibliothèques à partir de Code fiable](http://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [demandes](http://msdn.microsoft.com/en-us/e5283e28-2366-4519-b27d-ef5c1ddc1f48) [Demandes de liaison](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [données et modélisation](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



