---
title: 'CA2135 : Les assemblys de niveau 2 ne doivent pas contenir de LinkDemands | Microsoft Docs'
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
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 546a0e7bc14700863b5f5633938c7248a1292f5f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897262"
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
 À l’aide d’une classe ou un membre de classe un <xref:System.Security.Permissions.SecurityAction> dans une application qui utilise la sécurité de niveau 2.

## <a name="rule-description"></a>Description de la règle
 L’utilisation de LinkDemands est déconseillée dans l’ensemble de règles de sécurité de niveau 2. Au lieu d’utiliser LinkDemands pour implémenter la sécurité au moment de la compilation juste-à-temps (JIT), marquez les méthodes, types, champs et avec le <xref:System.Security.SecurityCriticalAttribute> attribut.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez le <xref:System.Security.Permissions.SecurityAction> et marquez le type ou le membre avec le <xref:System.Security.SecurityCriticalAttribute> attribut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 Dans l’exemple suivant, le <xref:System.Security.Permissions.SecurityAction> doivent être supprimés et la méthode marquée avec le <xref:System.Security.SecurityCriticalAttribute> attribut.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2135.securityrulesetlevel2methodsshouldnotbeprotectedwithlinkdemands/cs/ca2135.cs#1)]



