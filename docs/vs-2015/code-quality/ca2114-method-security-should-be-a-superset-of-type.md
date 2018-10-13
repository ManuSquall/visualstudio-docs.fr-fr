---
title: 'CA2114 : La sécurité de la méthode doit être un sur-ensemble du type | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: edc2d0961a107bb6d59006c9feb857f95499c9b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188201"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114 :La sécurité de la méthode doit être un sur-ensemble du type
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type a la sécurité déclarative et une de ses méthodes présente une sécurité déclarative pour la même action de sécurité, et l’action de sécurité n’est pas [demandes de liaison](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) ou [demandes d’héritage](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)et les autorisations vérifiées par le type ne sont pas un sous-ensemble des autorisations vérifiées par la méthode.

## <a name="rule-description"></a>Description de la règle
 Une méthode ne doit pas avoir à la fois une sécurité déclarative au niveau de la méthode et au niveau du type pour la même action. Les deux contrôles ne sont pas combinés ; uniquement la demande au niveau de la méthode est appliquée. Par exemple, si un type demande une autorisation `X`, et une de ses méthodes demande une autorisation `Y`, code n’a pas d’avoir l’autorisation `X` pour exécuter la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Passez en revue votre code pour vous assurer que les deux actions sont requises. Si les deux actions sont nécessaires, assurez-vous que l’action de niveau de la méthode inclut la sécurité spécifiée au niveau du type. Par exemple, si votre type demande une autorisation `X`, et sa méthode doit également demander une autorisation `Y`, la méthode doit demander explicitement `X` et `Y`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si la méthode ne requiert pas la sécurité spécifiée par le type. Toutefois, ce scénario n’est pas ordinaire et peut indiquer la nécessité d’un examen approfondi du design.

## <a name="example"></a>Exemple
 L’exemple suivant utilise des autorisations d’environnement pour illustrer les dangers de violation de cette règle. Dans cet exemple, le code d’application crée une instance du type sécurisé avant de refuser l’autorisation requise par le type. Dans un scénario de menace réel, l’application nécessiterait une autre façon d’obtenir une instance de l’objet.

 Dans l’exemple suivant, la bibliothèque demande autorisation en écriture pour un type et une autorisation pour une méthode de lecture.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Exemple
 Le code d’application suivant montre la vulnérabilité de la bibliothèque en appelant la méthode, même si elle ne répond pas aux exigences de sécurité de niveau type.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 Cet exemple produit la sortie suivante.

 **[Toutes les autorisations] Informations personnelles : 16/6/1964 12:00:00 AM**
 **[aucune autorisation d’écriture (exigée par type)] informations personnelles : 16/6/1964 12:00:00 AM**
 **[pas de lecture (d’autorisation exigée par méthode]) ne peut pas accéder aux informations personnelles : échouée de la requête.**
## <a name="see-also"></a>Voir aussi
 [Instructions de codage sécurisé](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [demandes d’héritage](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9) [demandes de liaison](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [données et modélisation](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



