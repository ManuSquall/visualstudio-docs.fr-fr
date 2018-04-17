---
title: 'CA2131 : Les types critiques de sécurité ne peuvent pas partie d’équivalence de type | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 551c0bd73abb2d42f2673dfcc57153b957bcbcbc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131 : Les types critiques de sécurité ne peuvent pas participer à l'équivalence des types
|||  
|-|-|  
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type participe à l’équivalence de type et un type lui-même, ou un membre ou champ du type, est marqué avec la <xref:System.Security.SecurityCriticalAttribute> attribut.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle se déclenche sur tout type ou type critique contenant des méthodes critiques ou des champs qui participent à l'équivalence de type. Lorsque le CLR détecte un tel type, il ne parvient pas à le charger avec une <xref:System.TypeLoadException> en cours d’exécution. En général, cette règle se déclenche uniquement lorsque les utilisateurs implémentent l'équivalence de type manuellement plutôt qu'en comptant sur tlbimp et les compilateurs pour faire l'équivalence de type.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez l’attribut SecurityCritical.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 Les exemples suivants montrent une interface, une méthode et un champ qui fait que cette règle s’applique.  
  
 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Code Transparent de sécurité, niveau 2](/dotnet/framework/misc/security-transparent-code-level-2)