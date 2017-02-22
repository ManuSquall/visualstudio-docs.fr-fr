---
title: "CA2138&#160;: Les m&#233;thodes transparentes ne doivent pas appeler les m&#233;thodes ayant l&#39;attribut SuppressUnmanagedCodeSecurity | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2138"
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2138&#160;: Les m&#233;thodes transparentes ne doivent pas appeler les m&#233;thodes ayant l&#39;attribut SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|CheckId|CA2138|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode transparente de sécurité appelle une méthode marquée avec l'attribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>.  
  
## Description de la règle  
 Cette règle déclenche sur toute méthode transparente qui fait directement appel au code natif, par exemple via un appel P\/Invoke \(appel de code\).  Les méthodes P\/Invoke et COM Interop marquées avec l'attribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> produisent un LinkDemand effectué sur la méthode d'appel.  Parce que le code transparent de sécurité ne peut pas satisfaire LinkDemands, le code ne peut pas également appeler les méthodes marquées avec l'attribut SuppressUnmanagedCodeSecurity, ou les méthodes de classe marquée avec l'attribut SuppressUnmanagedCodeSecurity.  La méthode échouera ou la demande sera convertie en demande complète.  
  
 Les violations de cette règle provoquent une <xref:System.MethodAccessException> dans le modèle de transparence de sécurité de niveau 2, et une demande complète pour <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> dans le modèle de transparence de niveau 1.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, supprimez l'attribut <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> et marquez la méthode avec l'attribut <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 [!code-cs[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]