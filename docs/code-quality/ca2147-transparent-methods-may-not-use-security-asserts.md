---
title: "CA2147 : Les méthodes transparentes ne peuvent pas utiliser d'assertions de sécurité"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SecurityTransparentCodeShouldNotAssert
- CA2147
- CA2128
helpviewer_keywords:
- CA2128
- SecurityTransparentCodeShouldNotAssert
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f732e22d53b4d469f73c4ef3efc753240fa6841f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31918095"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147 : Les méthodes transparentes ne peuvent pas utiliser d'assertions de sécurité
|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Code qui est marqué comme étant <xref:System.Security.SecurityTransparentAttribute> ne bénéficie pas des autorisations suffisantes pour déclarer.

## <a name="rule-description"></a>Description de la règle
 Cette règle analyse toutes les méthodes et les types dans un assembly qui est soit 100 % transparent ou/mi-critique et signale toutes les utilisations déclaratives ou impératives de <xref:System.Security.CodeAccessPermission.Assert%2A>.

 À l’exécution, tous les appels à <xref:System.Security.CodeAccessPermission.Assert%2A> à partir du code transparent provoquera un <xref:System.InvalidOperationException> levée. Cela peut se produire dans les deux assemblys transparents de 100 % et également dans les assemblys mixtes/mi-critique où une méthode ou un type est déclaré transparent, mais inclut une assertion utilisations déclarative ou impérative.

 Le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 a introduit une fonctionnalité nommée *transparence*. Types, champs, interfaces, classes et méthodes individuelles peuvent être transparent ou critique.

 Le code transparent ne peut pas élever les privilèges de sécurité. Par conséquent, toutes les autorisations accordées ou sollicitées sont automatiquement transmises via le code pour le domaine d’application appelant ou l’hôte. Exemples d’élévations incluent les assertions, les LinkDemands, l’attribut SuppressUnmanagedCode et `unsafe` code.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre ce problème, marquez le code qui appelle la méthode Assert avec la <xref:System.Security.SecurityCriticalAttribute>, ou supprimez l’assertion.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un message de cette règle.

## <a name="example"></a>Exemple
 Ce code échoue si `SecurityTestClass` est transparent, lorsque la `Assert` méthode lève une exception un <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>Exemple
 Une option consiste à la révision du code la méthode comme dans l’exemple ci-dessous et si la méthode est considérée comme sécurisée pour l’élévation, la marquer comme avec critique sécurisée Ceci nécessite qu’une sécurité détaillée, complet et sans erreur audit doit être effectué sur la méthode, ainsi que toutes les légendes qui se produisent dans la méthode de l’assertion :

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

 Une autre option consiste à supprimer l’assertion à partir du code et permettent de n’importe quel fichier flux de demandes d’autorisation d’e/s au-delà comme à l’appelant. Cela permet des vérifications de sécurité. Dans ce cas, aucun audit de sécurité n’est généralement nécessaire, car les demandes d’autorisation seront acheminées vers l’appelant et/ou le domaine d’application. Demandes d’autorisation sont étroitement contrôlés via la stratégie de sécurité, d’environnement et du code à la source.

## <a name="see-also"></a>Voir aussi
 [Avertissements liés à la sécurité](../code-quality/security-warnings.md)