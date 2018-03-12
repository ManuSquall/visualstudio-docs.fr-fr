---
title: "CA2141 : les méthodes transparentes ne répondent pas aux LinkDemands | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 938bda4d4b5c96b9627cf11aae81c51d269c0e5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>CA2141 : Les méthodes transparentes ne répondent pas aux LinkDemands
|||  
|-|-|  
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode transparente de sécurité appelle une méthode dans un assembly qui n’est pas marqué avec le <xref:System.Security.AllowPartiallyTrustedCallersAttribute> ) l’attribut APTCA (ou une méthode transparente de sécurité satisfait une <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` pour un type ou une méthode.  
  
## <a name="rule-description"></a>Description de la règle  
 Répondre à un LinkDemand est une opération de sécurité sensibles qui peut entraîner l’élévation de privilèges involontaire. Code transparent de sécurité ne doit pas répondre aux LinkDemands, car il n’est pas soumis aux mêmes exigences d’audit de sécurité que le code critique de sécurité. Les méthodes transparentes dans des assemblys de niveau 1 de sécurité règle ensemble entraîne tous les LinkDemands qu’ils satisfont en demandes complètes au moment de l’exécution, ce qui peut entraîner des problèmes de performances. Assemblys de niveau 2 de jeu de règle de sécurité, les méthodes transparentes ne parviendra pas à compiler dans le de compilateur juste-à-temps (JIT) s’ils tentent de répondre à une LinkDemand.  
  
 Dans les assemblys qui usee de sécurité de niveau 2, les tentatives par une méthode transparente de sécurité pour satisfaire un LinkDemand ou appeler une méthode dans un assembly non APTCA déclenche un <xref:System.MethodAccessException>; dans les assemblys de niveau 1 le LinkDemand devient une demande complète.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, marquez la méthode d’accès avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> d’attribut, ou supprimez le LinkDemand de la méthode accédée.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, une méthode transparente essaie d’appeler une méthode qui a un LinkDemand. Cette règle se déclenche sur ce code.  
  
 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]