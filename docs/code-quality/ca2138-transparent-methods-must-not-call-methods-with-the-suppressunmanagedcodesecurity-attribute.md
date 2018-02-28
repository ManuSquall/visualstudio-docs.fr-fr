---
title: "CA2138 : Les méthodes transparentes ne doivent pas appeler de méthodes avec l’attribut SuppressUnmanagedCodeSecurity | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0cef17ce232582cd23f961850bd52c048479e849
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
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
 Cette règle se déclenche sur toute méthode transparente qui appelle directement en code natif, par exemple, en utilisant un via un appel P/Invoke (non managé) appeler. Méthodes P/Invoke et COM interop sont marqués avec le <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribut produisent un LinkDemand effectué sur la méthode d’appel. Étant donné que le code transparent de sécurité ne peut pas répondre aux LinkDemands, le code ne peut pas également appeler les méthodes marquées avec l’attribut SuppressUnmanagedCodeSecurity ou les méthodes de classe marquée avec l’attribut SuppressUnmanagedCodeSecurity. La méthode échoue ou que la demande sera convertie en une demande complète.  
  
 Les violations de cette règle provoquent une <xref:System.MethodAccessException> dans le modèle de transparence de sécurité de niveau 2 et une demande complète pour <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> dans le modèle de transparence de niveau 1.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez le <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> d’attribut et marquez la méthode avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> attribut.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]