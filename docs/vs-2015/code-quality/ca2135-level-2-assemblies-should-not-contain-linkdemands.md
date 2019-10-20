---
title: 'CA2135 : les assemblys de niveau 2 ne doivent pas contenir de LinkDemands | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1248ac41a757ba2fc26ef0659c0f93ee325bc605
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602947"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135 : Les assemblys de niveau 2 ne doivent pas contenir de LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une classe ou un membre de classe utilise un <xref:System.Security.Permissions.SecurityAction> dans une application qui utilise la sécurité de niveau 2.

## <a name="rule-description"></a>Description de la règle
 L’utilisation de LinkDemands est déconseillée dans l’ensemble de règles de sécurité de niveau 2. Au lieu d’utiliser LinkDemands pour appliquer la sécurité au moment de la compilation juste-à-temps (JIT), marquez les méthodes, types et champs avec l’attribut <xref:System.Security.SecurityCriticalAttribute>.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez le <xref:System.Security.Permissions.SecurityAction> et marquez le type ou le membre avec l’attribut <xref:System.Security.SecurityCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, la <xref:System.Security.Permissions.SecurityAction> doit être supprimée et la méthode marquée avec l’attribut <xref:System.Security.SecurityCriticalAttribute>.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2135.securityrulesetlevel2methodsshouldnotbeprotectedwithlinkdemands/cs/ca2135.cs#1)]
