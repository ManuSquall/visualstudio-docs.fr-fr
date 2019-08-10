---
title: 'CA2147 : Les méthodes transparentes ne peuvent pas utiliser d’assertions de sécurité'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1b56001f5a083317911edde9282b66758deb1b6
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920727"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147 : Les méthodes transparentes ne peuvent pas utiliser d’assertions de sécurité

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Catégorie|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Le code marqué comme <xref:System.Security.SecurityTransparentAttribute> ne dispose pas des autorisations suffisantes pour Assert.

## <a name="rule-description"></a>Description de la règle
Cette règle analyse toutes les méthodes et tous les types d’un assembly qui est soit 100% transparent, soit mi-transparent/critique, et signale toute <xref:System.Security.CodeAccessPermission.Assert%2A>utilisation déclarative ou impérative de.

Au moment de l’exécution, tous <xref:System.Security.CodeAccessPermission.Assert%2A> les appels à à partir du <xref:System.InvalidOperationException> code transparent provoquent la levée d’une. Cela peut se produire dans les assemblys transparents 100%, ainsi que dans les assemblys mixtes transparents/critiques où une méthode ou un type est déclaré transparent, mais qui comprend une assertion déclarative ou impérative.

Le .NET Framework 2,0 a introduit une fonctionnalité nommée *transparence*. Les méthodes, les champs, les interfaces, les classes et les types individuels peuvent être transparents ou critiques.

Le code transparent n’est pas autorisé à élever les privilèges de sécurité. Par conséquent, toutes les autorisations accordées ou demandées sont automatiquement transmises via le code à l’appelant ou au domaine d’application hôte. Les assertions, LinkDemands, SuppressUnmanagedCode et `unsafe` code sont des exemples d’élévations.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour résoudre le problème, marquez le code qui appelle l’assertion avec le <xref:System.Security.SecurityCriticalAttribute>ou supprimez l’assertion.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez pas un message de cette règle.

## <a name="example"></a>Exemple
Ce code échoue si `SecurityTestClass` est transparent, lorsque la `Assert` méthode lève une <xref:System.InvalidOperationException>.

[!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>Exemple
L’une des options consiste à examiner le code de la méthode SecurityTransparentMethod dans l’exemple ci-dessous, et si la méthode est considérée comme sécurisée pour l’élévation, Mark SecurityTransparentMethod avec Secure-Critical. Pour cela, vous devez effectuer un audit de sécurité détaillé, complet et sans erreur sur la méthode, ainsi que tous les appels qui se produisent dans la méthode sous l’assertion:

[!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

Une autre option consiste à supprimer l’assertion du code et à laisser les demandes d’autorisations d’e/s de fichier ultérieures dépassant les SecurityTransparentMethod à l’appelant. Cela permet de vérifier la sécurité. Dans ce cas, aucun audit de sécurité n’est nécessaire, car les demandes d’autorisation sont transmises à l’appelant et/ou au domaine d’application. Les demandes d’autorisation sont étroitement contrôlées par le biais de la stratégie de sécurité, de l’environnement d’hébergement et des autorisations d’autorisation de source de code.

## <a name="see-also"></a>Voir aussi
[Avertissements liés à la sécurité](../code-quality/security-warnings.md)