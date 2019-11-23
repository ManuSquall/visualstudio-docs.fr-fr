---
title: 'CA2116 : les méthodes APTCA doivent uniquement appeler des méthodes APTCA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
helpviewer_keywords:
- AptcaMethodsShouldOnlyCallAptcaMethods
- CA2116
ms.assetid: 8b91637e-891f-4dde-857b-bf8012270ec4
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c9de5178b585275ef410ad3179ba320b663536bf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658680"
---
# <a name="ca2116-aptca-methods-should-only-call-aptca-methods"></a>CA2116 : Les méthodes APTCA doivent uniquement appeler des méthodes APTCA
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AptcaMethodsShouldOnlyCallAptcaMethods|
|CheckId|CA2116|
|Catégorie|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode dans un assembly avec l’attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName> appelle une méthode dans un assembly qui n’a pas l’attribut.

## <a name="rule-description"></a>Description de la règle
 Par défaut, les méthodes publiques ou protégées des assemblys avec des noms forts sont protégées implicitement par une [demande de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) pour une confiance totale. Seuls les appelants d’un niveau de confiance suffisant peuvent accéder à un assembly avec nom fort. Les assemblys avec nom fort marqués avec l’attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) n’ont pas cette protection. L’attribut désactive la demande de liaison, ce qui rend l’assembly accessible aux appelants qui ne bénéficient pas d’une confiance totale, tels que le code qui s’exécute à partir d’un intranet ou d’Internet.

 Lorsque l’attribut APTCA est présent dans un assembly entièrement fiable et que l’assembly exécute du code dans un autre assembly qui n’autorise pas les appelants d’un niveau de confiance partiel, une faille de sécurité est possible. Si deux méthodes `M1` et `M2` remplissent les conditions suivantes, les appelants malveillants peuvent utiliser la méthode `M1` pour contourner la demande de liaison de confiance totale implicite qui protège `M2`:

- `M1` est une méthode publique déclarée dans un assembly de confiance totale qui a l’attribut APTCA.

- `M1` appelle une méthode `M2` l’assembly `M1`.

- l’assembly de `M2`n’a pas l’attribut APTCA et, par conséquent, ne doit pas être exécuté par ou pour le compte des appelants qui ont un niveau de confiance partiel.

  Un appelant de confiance partielle `X` peut appeler la méthode `M1`, ce qui provoque l’appel de `M1` `M2`. Étant donné que `M2` n’a pas l’attribut APTCA, son appelant immédiat (`M1`) doit satisfaire une demande de liaison pour une confiance totale. `M1` dispose d’une confiance totale et, par conséquent, est conforme à cette vérification. Le risque de sécurité est dû au fait que `X` ne participe pas à la satisfaction de la demande de liaison qui protège `M2` des appelants non fiables. Par conséquent, les méthodes avec l’attribut APTCA ne doivent pas appeler de méthodes qui n’ont pas l’attribut.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Si l’attribut APCTA est requis, utilisez une demande pour protéger la méthode qui appelle l’assembly de confiance totale. Les autorisations exactes que vous demandez dépendent de la fonctionnalité exposée par votre méthode. Si possible, Protégez la méthode avec une demande de confiance totale pour garantir que la fonctionnalité sous-jacente n’est pas exposée aux appelants d’un niveau de confiance partiel. Si ce n’est pas possible, sélectionnez un ensemble d’autorisations qui protègent efficacement les fonctionnalités exposées. Pour plus d’informations sur les demandes, consultez [demandes](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que la fonctionnalité exposée par votre méthode ne permet pas directement ou indirectement aux appelants d’accéder à des informations sensibles, à des opérations ou à des ressources qui peuvent être utilisées de manière destructrice.

## <a name="example"></a>Exemple
 L’exemple suivant utilise deux assemblys et une application de test pour illustrer la vulnérabilité de sécurité détectée par cette règle. Le premier assembly n’a pas l’attribut APTCA et ne doit pas être accessible aux appelants de confiance partielle (représenté par `M2` dans la discussion précédente).

 [!code-csharp[FxCop.Security.NoAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.NoAptca/cs/FxCop.Security.NoAptca.cs#1)]

## <a name="example"></a>Exemple
 Le deuxième assembly est entièrement fiable et autorise les appelants d’un niveau de confiance partiel (représenté par `M1` dans la discussion précédente).

 [!code-csharp[FxCop.Security.YesAptca#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.YesAptca/cs/FxCop.Security.YesAptca.cs#1)]

## <a name="example"></a>Exemple
 L’application de test (représentée par `X` dans la discussion précédente) est de confiance partielle.

 [!code-csharp[FxCop.Security.TestAptcaMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestAptcaMethods/cs/FxCop.Security.TestAptcaMethods.cs#1)]

 Cet exemple produit la sortie suivante.

 **Demande de confiance totale : échec de la requête.** 
**ClassRequiringFullTrust. reswork a été appelé.**
## <a name="related-rules"></a>Règles associées
 [CA2117 : Les types APTCA doivent étendre seulement des types de base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)

## <a name="see-also"></a>Voir aussi
 [Instructions de codage sécurisé](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [.NET Framework assemblys pouvant être appelés par du code](https://msdn.microsoft.com/a417fcd4-d3ca-4884-a308-3a1a080eac8d) d’un point de confiance partiel [à l’aide de bibliothèques de code de confiance partielle](https://msdn.microsoft.com/library/dd66cd4c-b087-415f-9c3e-94e3a1835f74) [demandes](https://msdn.microsoft.com/e5283e28-2366-4519-b27d-ef5c1ddc1f48) de [liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [données et modélisation](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
