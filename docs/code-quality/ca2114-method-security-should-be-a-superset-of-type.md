---
title: 'CA2114 : La sécurité de la méthode doit être un sur-ensemble du type'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 536e676a1b2527c466aae741ca7117be507bfb9a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232754"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114 : La sécurité de la méthode doit être un sur-ensemble du type

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Un type a une sécurité déclarative et l’une de ses méthodes a une sécurité déclarative pour la même action de sécurité, et l’action de sécurité n’est pas une [demande de liaison](/dotnet/framework/misc/link-demands), et les autorisations vérifiées par le type ne sont pas un sous-ensemble des autorisations contrôlées par la méthode.

## <a name="rule-description"></a>Description de la règle
Une méthode ne doit pas avoir à la fois une sécurité déclarative au niveau de la méthode et au niveau du type pour la même action. Les deux contrôles ne sont pas combinés ; seule la demande au niveau de la méthode est appliquée. Par exemple, si un type demande une `X`autorisation et que l’une de ses méthodes `Y`demande une autorisation, le code n’a `X` pas besoin d’avoir l’autorisation d’exécuter la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Examinez votre code pour vous assurer que les deux actions sont requises. Si les deux actions sont requises, assurez-vous que l’action au niveau de la méthode comprend la sécurité spécifiée au niveau du type. Par exemple, si votre type demande une `X`autorisation et que sa méthode doit également demander `Y`une autorisation, la méthode doit `X` demander `Y`explicitement et.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle si la méthode ne requiert pas la sécurité spécifiée par le type. Toutefois, il ne s’agit pas d’un scénario ordinaire et peut indiquer une nécessité d’un examen minutieux de la conception.

## <a name="example-1"></a>Exemple 1

L’exemple suivant utilise des autorisations d’environnement pour démontrer les dangers de la violation de cette règle. Dans cet exemple, le code d’application crée une instance du type sécurisé avant de refuser l’autorisation requise par le type. Dans un scénario de menace réel, l’application nécessiterait une autre façon d’obtenir une instance de l’objet.

Dans l’exemple suivant, la bibliothèque demande une autorisation d’écriture pour un type et une autorisation de lecture pour une méthode.

[!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example-2"></a>Exemple 2

Le code d’application suivant illustre la vulnérabilité de la bibliothèque en appelant la méthode, même si elle ne répond pas aux exigences de sécurité au niveau du type.

[!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

Cet exemple génère la sortie suivante :

```txt
[All permissions] Personal information: 6/16/1964 12:00:00 AM
[No write permission (demanded by type)] Personal information: 6/16/1964 12:00:00 AM
[No read permission (demanded by method)] Could not access personal information: Request failed.
```

## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)
- [Demandes de liaison](/dotnet/framework/misc/link-demands)
- [Données et modélisation](/dotnet/framework/data/index)