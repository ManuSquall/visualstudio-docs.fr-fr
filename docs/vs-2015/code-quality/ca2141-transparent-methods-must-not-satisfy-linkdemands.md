---
title: 'CA2141 : les méthodes transparentes ne répondent pas aux LinkDemands | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a7c54b472e91aa2be1d8e5bb1a9c32c26c0cb299
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142703"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141 : Les méthodes transparentes ne répondent pas aux LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Catégorie|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode transparente de sécurité appelle une méthode dans un assembly qui n’est pas marqué avec le <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribut (APTCA), ou une méthode transparente de sécurité satisfait une <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` pour un type ou une méthode.

## <a name="rule-description"></a>Description de la règle
 Répondre à un LinkDemand est une opération de sécurité sensibles ce qui peut entraîner l’élévation de privilèges involontaire. Code transparent de sécurité ne doit pas répondre aux LinkDemands, car il n’est pas soumis aux mêmes exigences d’audit de sécurité en tant que code critique de sécurité. Les méthodes transparentes dans les assemblys de niveau 1 jeu sécurité règle entraîne tous les LinkDemands qu’ils satisfont en demandes complètes au moment de l’exécution, ce qui peut entraîner des problèmes de performances. Dans les assemblys de niveau 2 d’ensemble de règles de sécurité, les méthodes transparentes échoue à compiler dans le compilateur juste-à-temps (JIT) si elles essaient de satisfaire un LinkDemand.

 Dans les assemblys qu’usee sécurité de niveau 2, les tentatives par une méthode transparente de sécurité pour satisfaire un LinkDemand ou appeler une méthode dans un assembly non-APTCA déclenche un <xref:System.MethodAccessException>; dans les assemblys de niveau 1 le LinkDemand devient une demande complète.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, marquez la méthode d’accès avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> d’attribut, ou supprimez le LinkDemand de la méthode accédée.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 Dans cet exemple, une méthode transparente essaie d’appeler une méthode qui a un LinkDemand. Cette règle se déclenche sur ce code.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]
