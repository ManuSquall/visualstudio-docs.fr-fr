---
title: 'CA2114 : Sécurité de la méthode doit être un sur-ensemble du type'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec58e8060447a02309a0a902bcf63eea8805ca8c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53881790"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114 : Sécurité de la méthode doit être un sur-ensemble du type

|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type a la sécurité déclarative et une de ses méthodes présente une sécurité déclarative pour la même action de sécurité, et l’action de sécurité n’est pas [demandes de liaison](/dotnet/framework/misc/link-demands), et les autorisations vérifiées par le type ne sont pas un sous-ensemble des autorisations vérifié par la méthode.

## <a name="rule-description"></a>Description de la règle
 Une méthode ne doit pas avoir à la fois une sécurité déclarative au niveau de la méthode et au niveau du type pour la même action. Les deux contrôles ne sont pas combinés ; uniquement la demande au niveau de la méthode est appliquée. Par exemple, si un type demande une autorisation `X`, et une de ses méthodes demande une autorisation `Y`, code n’a pas d’avoir l’autorisation `X` pour exécuter la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Passez en revue votre code pour vous assurer que les deux actions sont requises. Si les deux actions sont nécessaires, assurez-vous que l’action de niveau de la méthode inclut la sécurité spécifiée au niveau du type. Par exemple, si votre type demande une autorisation `X`, et sa méthode doit également demander une autorisation `Y`, la méthode doit demander explicitement `X` et `Y`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si la méthode ne requiert pas la sécurité spécifiée par le type. Toutefois, ce scénario n’est pas ordinaire et peut indiquer la nécessité d’un examen approfondi du design.

## <a name="example-1"></a>Exemple 1

L’exemple suivant utilise des autorisations d’environnement pour illustrer les dangers de violation de cette règle. Dans cet exemple, le code d’application crée une instance du type sécurisé avant de refuser l’autorisation requise par le type. Dans un scénario de menace réel, l’application nécessiterait une autre façon d’obtenir une instance de l’objet.

Dans l’exemple suivant, la bibliothèque demande autorisation en écriture pour un type et une autorisation pour une méthode de lecture.

[!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example-2"></a>Exemple 2

Le code d’application suivant montre la vulnérabilité de la bibliothèque en appelant la méthode, même si elle ne répond pas aux exigences de sécurité de niveau type.

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