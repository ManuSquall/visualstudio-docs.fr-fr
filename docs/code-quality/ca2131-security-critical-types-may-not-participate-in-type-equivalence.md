---
title: "CA2131 : Les types critiques de sécurité ne peuvent pas participer à l'équivalence des types"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 521a44b432a5b8ea886b23aab6b39789efe3b1b0
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920711"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131 : Les types critiques de sécurité ne peuvent pas participer à l'équivalence des types

|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|Catégorie|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Un type participe à l’équivalence de type et un type lui-même, ou un membre ou champ du type, est marqué avec l' <xref:System.Security.SecurityCriticalAttribute> attribut.

## <a name="rule-description"></a>Description de la règle
Cette règle se déclenche sur tout type ou type critique contenant des méthodes critiques ou des champs qui participent à l’équivalence de type. Lorsque le CLR détecte un tel type, il ne peut pas le charger avec un <xref:System.TypeLoadException> au moment de l’exécution. En général, cette règle se déclenche uniquement lorsque les utilisateurs implémentent l’équivalence de type manuellement plutôt qu’en comptant sur tlbimp et les compilateurs pour faire l’équivalence de type.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, supprimez l’attribut SecurityCritical.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
Les exemples suivants illustrent une interface, une méthode et un champ qui entraîne le déclenchement de cette règle.

[!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]

## <a name="see-also"></a>Voir aussi
[Code transparent de sécurité, niveau 2](/dotnet/framework/misc/security-transparent-code-level-2)