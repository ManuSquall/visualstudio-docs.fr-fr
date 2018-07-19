---
title: CA2114 :La sécurité de la méthode doit être un sur-ensemble du type
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.openlocfilehash: 5d2fc6fb60dd837dd93de1db2758ee0e2c216850
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914950"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114 :La sécurité de la méthode doit être un sur-ensemble du type
|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type a la sécurité déclarative, une de ses méthodes présente une sécurité déclarative pour la même action de sécurité et l’action de sécurité n’est pas [les demandes de liaison](/dotnet/framework/misc/link-demands), et les autorisations vérifiées par le type ne sont pas un sous-ensemble des autorisations vérifiée par la méthode.

## <a name="rule-description"></a>Description de la règle
 Une méthode ne doit pas avoir à la fois une sécurité déclarative au niveau méthode et au niveau type pour la même action. Les deux contrôles ne sont pas combinés ; uniquement la demande de niveau de la méthode est appliquée. Par exemple, si un type demande une autorisation `X`, et une de ses méthodes demande une autorisation `Y`, code ne doit pas avoir l’autorisation `X` pour exécuter la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Examinez votre code pour vous assurer que les deux actions sont requises. Si les deux actions sont requises, assurez-vous que l’action de niveau de la méthode inclut la sécurité spécifiée au niveau du type. Par exemple, si votre type demande une autorisation `X`, et sa méthode doit également demander une autorisation `Y`, la méthode doit demander explicitement `X` et `Y`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si la méthode ne requiert pas la sécurité spécifiée par le type. Toutefois, ce scénario n’est pas ordinaire et peut indiquer la nécessité d’un examen approfondi du design.

## <a name="example"></a>Exemple
 L’exemple suivant utilise des autorisations d’environnement pour illustrer les risques de violation de cette règle. Dans cet exemple, le code d’application crée une instance du type sécurisé avant de refuser l’autorisation requise par le type. Dans un scénario de menace réel, l’application nécessite une autre méthode pour obtenir une instance de l’objet.

 Dans l’exemple suivant, la bibliothèque demande autorisation d’écriture pour un type et une autorisation pour une méthode de lecture.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]

## <a name="example"></a>Exemple
 Le code d’application suivant montre la vulnérabilité de la bibliothèque en appelant la méthode, même si elle ne répond pas aux exigences de sécurité de niveau type.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]

 Cet exemple produit la sortie suivante.

 **[Toutes les autorisations] Informations personnelles : 6/16/1964 12:00:00 AM**
 **[aucune autorisation d’écriture (exigée par type)] les informations personnelles : 6/16/1964 12:00:00 AM**
 **[pas de lecture (de l’autorisation exigée par méthode]) ne peut pas accéder aux données personnelles : échouée de la demande.**
## <a name="see-also"></a>Voir aussi
 [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines) [demandes de liaison](/dotnet/framework/misc/link-demands) [données et modélisation](/dotnet/framework/data/index)