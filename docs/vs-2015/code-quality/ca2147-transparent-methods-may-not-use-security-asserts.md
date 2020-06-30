---
title: 'CA2147 : les méthodes transparentes ne peuvent pas utiliser d’assertions de sécurité | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 45639afc9946aa43df121a5a1881174371413c25
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546378"
---
# <a name="ca2147-transparent-methods-may-not-use-security-asserts"></a>CA2147 : Les méthodes transparentes ne peuvent pas utiliser d’assertions de sécurité
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|SecurityTransparentCodeShouldNotAssert|
|CheckId|CA2147|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Le code marqué comme ne <xref:System.Security.SecurityTransparentAttribute> dispose pas des autorisations suffisantes pour Assert.

## <a name="rule-description"></a>Description de la règle
 Cette règle analyse toutes les méthodes et tous les types dans un assembly qui est de 100% transparent ou mi-transparent/critique, et signale toutes les utilisations déclaratives ou impératives de <xref:System.Security.CodeAccessPermission.Assert%2A> .

 Au moment de l’exécution, tous les appels à <xref:System.Security.CodeAccessPermission.Assert%2A> à partir du code transparent provoquent la <xref:System.InvalidOperationException> levée d’une. Cela peut se produire dans les assemblys transparents 100%, ainsi que dans les assemblys mixtes transparents/critiques où une méthode ou un type est déclaré transparent, mais qui comprend une assertion déclarative ou impérative.

 Le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2,0 a introduit une fonctionnalité nommée *transparence*. Les méthodes, les champs, les interfaces, les classes et les types individuels peuvent être transparents ou critiques.

 Le code transparent n’est pas autorisé à élever les privilèges de sécurité. Par conséquent, toutes les autorisations accordées ou demandées sont automatiquement transmises via le code à l’appelant ou au domaine d’application hôte. Les assertions, LinkDemands, SuppressUnmanagedCode et code sont des exemples d’élévations `unsafe` .

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour résoudre le problème, marquez le code qui appelle l’assertion avec le <xref:System.Security.SecurityCriticalAttribute> ou supprimez l’assertion.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un message de cette règle.

## <a name="example"></a>Exemple
 Ce code échoue si `SecurityTestClass` est transparent, lorsque la `Assert` méthode lève une <xref:System.InvalidOperationException> .

 [!code-csharp[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts/cs/ca2147 - transparentmethodsmustnotusesecurityasserts.cs#1)]

## <a name="example"></a>Exemple
 L’une des options consiste à examiner le code de la méthode SecurityTransparentMethod dans l’exemple ci-dessous. Si la méthode est considérée comme sécurisée pour l’élévation, marquez SecurityTransparentMethod avec Secure-Critical. cela requiert qu’un audit de sécurité détaillé, complet et sans erreur doive être exécuté sur la méthode ainsi que tous les appels qui se produisent dans la méthode sous l’assertion :

 [!code-csharp[FxCop.Security.SecurityTransparentCode2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2/cs/FxCop.Security.SecurityTransparentCode2.cs#1)]

 Une autre option consiste à supprimer l’assertion du code et à laisser les demandes d’autorisations d’e/s de fichier ultérieures dépassant les SecurityTransparentMethod à l’appelant. Cela permet de vérifier la sécurité. Dans ce cas, aucun audit de sécurité n’est généralement nécessaire, car les demandes d’autorisation sont transmises à l’appelant et/ou au domaine d’application. Les demandes d’autorisation sont étroitement contrôlées par le biais de la stratégie de sécurité, de l’environnement d’hébergement et des autorisations d’autorisation de source de code.

## <a name="see-also"></a>Voir aussi
 [Avertissements de sécurité](../code-quality/security-warnings.md)
