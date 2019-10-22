---
title: 'Ca2138 : les méthodes transparentes ne doivent pas appeler de méthodes avec l’attribut SuppressUnmanagedCodeSecurity | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 65e00d319bff3bbfd3c441c6b60ed8a703e69251
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654811"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138 : Les méthodes transparentes ne doivent pas appeler les méthodes ayant l'attribut SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode transparente de sécurité appelle une méthode marquée avec l’attribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.

## <a name="rule-description"></a>Description de la règle
 Cette règle se déclenche sur toute méthode transparente qui appelle directement en code natif, par exemple, à l’aide d’un via un appel P/Invoke (appel de code non managé). Les méthodes P/Invoke et COM Interop qui sont marquées avec l’attribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> entraînent la réalisation d’un LinkDemand sur la méthode appelante. Étant donné que le code transparent de sécurité ne peut pas satisfaire les LinkDemands, le code ne peut pas non plus appeler les méthodes marquées avec l’attribut SuppressUnmanagedCodeSecurity, ou les méthodes de la classe qui est marquée avec l’attribut SuppressUnmanagedCodeSecurity. La méthode échoue ou la demande est convertie en une demande complète.

 Les violations de cette règle conduisent à une <xref:System.MethodAccessException> dans le modèle de transparence de sécurité de niveau 2 et à une demande complète de <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> dans le modèle de transparence de niveau 1.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez l’attribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> et marquez la méthode avec l’attribut <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]
