---
title: 'CA2114 : la sécurité de la méthode doit être un sur-ensemble de type | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MethodSecurityShouldBeASupersetOfType
- CA2114
helpviewer_keywords:
- CA2114
- MethodSecurityShouldBeASupersetOfType
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d7879d8b2aa9eb4ece1ce07f89681b6c0b0f5f31
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534704"
---
# <a name="ca2114-method-security-should-be-a-superset-of-type"></a>CA2114 : La sécurité de la méthode doit être un sur-ensemble du type
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|MethodSecurityShouldBeASupersetOfType|
|CheckId|CA2114|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 Un type a une sécurité déclarative et l’une de ses méthodes a une sécurité déclarative pour la même action de sécurité, et l’action de sécurité n’est pas une [demande de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) ou des [demandes d’héritage](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9), et les autorisations vérifiées par le type ne sont pas un sous-ensemble des autorisations contrôlées par la méthode.

## <a name="rule-description"></a>Description de la règle
 Une méthode ne doit pas avoir à la fois une sécurité déclarative au niveau de la méthode et au niveau du type pour la même action. Les deux contrôles ne sont pas combinés ; seule la demande au niveau de la méthode est appliquée. Par exemple, si un type demande une autorisation `X` et que l’une de ses méthodes demande une autorisation `Y` , le code n’a pas besoin d’avoir `X` l’autorisation d’exécuter la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Examinez votre code pour vous assurer que les deux actions sont requises. Si les deux actions sont requises, assurez-vous que l’action au niveau de la méthode comprend la sécurité spécifiée au niveau du type. Par exemple, si votre type demande une autorisation `X` et que sa méthode doit également demander une autorisation `Y` , la méthode doit demander explicitement `X` et `Y` .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si la méthode ne requiert pas la sécurité spécifiée par le type. Toutefois, il ne s’agit pas d’un scénario ordinaire et peut indiquer une nécessité d’un examen minutieux de la conception.

## <a name="example"></a>Exemple
 L’exemple suivant utilise des autorisations d’environnement pour démontrer les dangers de la violation de cette règle. Dans cet exemple, le code d’application crée une instance du type sécurisé avant de refuser l’autorisation requise par le type. Dans un scénario de menace réel, l’application nécessiterait une autre façon d’obtenir une instance de l’objet.

 Dans l’exemple suivant, la bibliothèque demande une autorisation d’écriture pour un type et une autorisation de lecture pour une méthode.

 [!code-csharp[FxCop.Security.MethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MethodLevelSecurity/cs/FxCop.Security.MethodLevelSecurity.cs#1)]

## <a name="example"></a>Exemple
 Le code d’application suivant illustre la vulnérabilité de la bibliothèque en appelant la méthode, même si elle ne répond pas aux exigences de sécurité au niveau du type.

 [!code-csharp[FxCop.Security.TestMethodLevelSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestMethodLevelSecurity/cs/FxCop.Security.TestMethodLevelSecurity.cs#1)]

 Cet exemple produit la sortie suivante.

 **[Toutes les autorisations] informations personnelles : 6/16/1964 12:00:00 AM** 
 **[Aucune autorisation d’écriture (exigée par type)] informations personnelles : 6/16/1964 12:00:00 AM** 
 **[Aucune autorisation de lecture (demandée par la méthode)] n’a pas pu accéder aux informations personnelles : la demande a échoué.**
## <a name="see-also"></a>Voir aussi
 [Instructions de codage sécurisé directives](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) d' [héritage demandes](https://msdn.microsoft.com/28b9adbb-8f08-4f10-b856-dbf59eb932d9) de [liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [données et modélisation](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
