---
title: "CA2138 : Les méthodes transparentes ne doivent pas appeler les méthodes ayant l'attribut SuppressUnmanagedCodeSecurity"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 3ba7a1c25387349ba78b198a37b709d6bdd10b64
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948628"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138 : Les méthodes transparentes ne doivent pas appeler les méthodes ayant l'attribut SuppressUnmanagedCodeSecurity

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode transparente de sécurité appelle une méthode marquée avec le <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribut.

## <a name="rule-description"></a>Description de la règle
 Cette règle se déclenche sur toute méthode transparente qui appelle directement en code natif, par exemple, à l’aide d’un P/Invoke (non managé) appeler. Méthodes P/Invoke et COM interop sont marqués avec le <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribut de résultat dans un LinkDemand effectué sur la méthode d’appel. Étant donné que le code transparent de sécurité ne peut pas satisfaire LinkDemands, le code ne peut pas également appeler les méthodes marquées avec l’attribut SuppressUnmanagedCodeSecurity, ou des méthodes de classe qui est marquée avec l’attribut SuppressUnmanagedCodeSecurity. La méthode échoue, ou à la demande sera convertie en une demande complète.

 Les violations de cette règle provoquent une <xref:System.MethodAccessException> dans le modèle de transparence de sécurité de niveau 2 et une demande complète pour <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> dans le modèle de transparence de niveau 1.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez le <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> d’attribut et marquez la méthode avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> attribut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]