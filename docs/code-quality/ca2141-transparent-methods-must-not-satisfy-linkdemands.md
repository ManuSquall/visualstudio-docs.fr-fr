---
title: 'CA2141 : Les méthodes transparentes ne répondent pas aux LinkDemands'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a64e8acae7e7dd76107bc761a6b035f2963247fe
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
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