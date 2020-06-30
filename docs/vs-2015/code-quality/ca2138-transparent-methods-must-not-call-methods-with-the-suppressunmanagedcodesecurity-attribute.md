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
ms.openlocfilehash: 35cc152998b15a2fd4c4ff02e4730cdfae5366cb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546495"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138 : Les méthodes transparentes ne doivent pas appeler les méthodes ayant l'attribut SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode transparente de sécurité appelle une méthode qui est marquée avec l' <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribut.

## <a name="rule-description"></a>Description de la règle
 Cette règle se déclenche sur toute méthode transparente qui appelle directement en code natif, par exemple, à l’aide d’un via un appel P/Invoke (appel de code non managé). Les méthodes P/Invoke et COM Interop qui sont marquées avec l' <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribut entraînent la réalisation d’un LinkDemand sur la méthode appelante. Étant donné que le code transparent de sécurité ne peut pas satisfaire les LinkDemands, le code ne peut pas non plus appeler les méthodes marquées avec l’attribut SuppressUnmanagedCodeSecurity, ou les méthodes de la classe qui est marquée avec l’attribut SuppressUnmanagedCodeSecurity. La méthode échoue ou la demande est convertie en une demande complète.

 Les violations de cette règle entraînent une <xref:System.MethodAccessException> dans le modèle de transparence de sécurité de niveau 2 et une demande complète pour <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> dans le modèle de transparence de niveau 1.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez l' <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribut et marquez la méthode avec l' <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> attribut ou.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]
