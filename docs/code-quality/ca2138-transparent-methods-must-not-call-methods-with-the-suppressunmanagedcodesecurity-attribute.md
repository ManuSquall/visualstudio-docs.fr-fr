---
title: "CA2138 : Les méthodes transparentes ne doivent pas appeler les méthodes ayant l'attribut SuppressUnmanagedCodeSecurity"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 316aef3b0f1f715857fde8eaf2a6e74b1a49e40f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920577"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138 : Les méthodes transparentes ne doivent pas appeler les méthodes ayant l'attribut SuppressUnmanagedCodeSecurity

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Catégorie|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Une méthode transparente de sécurité appelle une méthode qui est marquée avec <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> l’attribut.

## <a name="rule-description"></a>Description de la règle
Cette règle se déclenche sur toute méthode transparente qui appelle directement dans le code natif, par exemple, à l’aide d’un appel P/Invoke (appel de code non managé). Les méthodes P/Invoke et COM Interop qui sont marquées <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> avec l’attribut entraînent la réalisation d’un LinkDemand sur la méthode appelante. Étant donné que le code transparent de sécurité ne peut pas satisfaire les LinkDemands, le code ne peut pas non plus appeler les méthodes marquées avec l’attribut SuppressUnmanagedCodeSecurity, ou les méthodes de la classe qui est marquée avec l’attribut SuppressUnmanagedCodeSecurity. La méthode échoue ou la demande est convertie en une demande complète.

Les violations de cette règle entraînent <xref:System.MethodAccessException> une dans le modèle de transparence de sécurité de niveau 2 et une <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> demande complète pour dans le modèle de transparence de niveau 1.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, supprimez <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> l’attribut et marquez la méthode <xref:System.Security.SecurityCriticalAttribute> avec l' <xref:System.Security.SecuritySafeCriticalAttribute> attribut ou.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemples
[!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]