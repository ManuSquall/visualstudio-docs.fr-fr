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
ms.openlocfilehash: 36ae392173a18796c53100599fbf5f5fb5997beb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796856"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147 : Les méthodes transparentes ne peuvent pas utiliser d’assertions de sécurité

|||
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Code qui est marqué comme <xref:System.Security.SecurityTransparentAttribute> n’est pas accordé les autorisations suffisantes pour déclarer.

## <a name="rule-description"></a>Description de la règle
 Cette règle analyse toutes les méthodes et les types dans un assembly qui est soit 100 % transparent ou mi-transparent mi-critique et elle signale toutes les utilisations déclaratives ou impératives de <xref:System.Security.CodeAccessPermission.Assert%2A>.

 À l’exécution, tous les appels à <xref:System.Security.CodeAccessPermission.Assert%2A> à partir du code transparent entraîne un <xref:System.InvalidOperationException> levée. Cela peut se produire dans les deux assemblys transparents de 100 %, ainsi que dans les assemblys mixtes mi-critique où une méthode ou le type est déclaré transparent, mais inclut une assertion déclarative ou impérative.

 Le .NET Framework 2.0 a introduit une fonctionnalité nommée *transparence*. Types de champs, interfaces, classes et méthodes individuelles peuvent être transparent ou critique.

 Code transparent n’est pas autorisé à élever les privilèges de sécurité. Par conséquent, toutes les autorisations accordées ou sollicitées sont automatiquement transmises via le code pour le domaine d’application appelant ou l’hôte. Exemples d’élévations incluent les assertions, les LinkDemands, l’attribut SuppressUnmanagedCode et `unsafe` code.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre ce problème, marquez le code qui appelle la méthode Assert avec le <xref:System.Security.SecurityCriticalAttribute>, ou supprimez l’assertion.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un message à partir de cette règle.

## <a name="example"></a>Exemple
 Ce code échouera si `SecurityTestClass` est transparent, lorsque la `Assert` méthode lève un <xref:System.InvalidOperationException>.

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]

## <a name="example"></a>Exemple
 Une option consiste à la révision du code la méthode comme dans l’exemple ci-dessous et si la méthode est considérée comme sûr pour l’élévation, à la marquer comme avec critique sécurisée. Cela nécessite qu’un audit de sécurité détaillés, complets et sans erreur doit être effectué sur la méthode ainsi que les légendes qui se produisent dans la méthode de l’assertion :

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]

 Une autre option consiste à supprimer l’assertion du code et permettent de n’importe quel flux de demandes d’autorisation d’e/s au-delà comme à l’appelant de fichier suivante. Cela permet des vérifications de sécurité. Dans ce cas, aucun audit de sécurité n’est nécessaire, car les demandes d’autorisation circulent à l’appelant et/ou le domaine d’application. Demandes d’autorisation sont étroitement contrôlés via la stratégie de sécurité, environnement d’hébergement et code à la source.

## <a name="see-also"></a>Voir aussi
 [Avertissements liés à la sécurité](../code-quality/security-warnings.md)