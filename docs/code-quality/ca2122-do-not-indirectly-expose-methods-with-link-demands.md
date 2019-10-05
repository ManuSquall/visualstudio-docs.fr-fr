---
title: "CA2122 : N'exposez pas indirectement des méthodes avec des demandes de liaison"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6850cee67a0dfed4b386eef5ed7cb021d3c76a4d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232513"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122 : N'exposez pas indirectement des méthodes avec des demandes de liaison

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un membre public ou protégé a des [demandes de liaison](/dotnet/framework/misc/link-demands) et est appelé par un membre qui n’effectue aucune vérification de sécurité.

## <a name="rule-description"></a>Description de la règle
Une demande de liaison vérifie uniquement les autorisations de l’appelant immédiat. Si un membre `X` ne fait aucune demande de sécurité de ses appelants et appelle du code protégé par une demande de liaison, un appelant sans l’autorisation `X` nécessaire peut utiliser pour accéder au membre protégé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Ajoutez des données de sécurité [et une modélisation](/dotnet/framework/data/index) ou une demande de liaison au membre afin qu’il ne fournisse plus d’accès non sécurisé au membre protégé à la demande de liaison.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que votre code n’accorde pas à ses appelants l’accès aux opérations ou aux ressources qui peuvent être utilisées de manière destructrice.

## <a name="example-1"></a>Exemple 1
Les exemples suivants illustrent une bibliothèque qui enfreint la règle et une application qui illustre la faiblesse de la bibliothèque. L’exemple de bibliothèque fournit deux méthodes qui enfreignent ensemble la règle. La `EnvironmentSetting` méthode est sécurisée par une demande de liaison pour un accès illimité aux variables d’environnement. La `DomainInformation` méthode ne fait aucune demande de sécurité de ses appelants avant `EnvironmentSetting`d’appeler.

[!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>Exemple 2
L’application suivante appelle le membre de bibliothèque non sécurisé.

[!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

Cet exemple génère la sortie suivante :

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)
- [Demandes de liaison](/dotnet/framework/misc/link-demands)
- [Données et modélisation](/dotnet/framework/data/index)