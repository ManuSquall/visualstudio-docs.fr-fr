---
title: "CA2142&#160;: Le code transparent ne doit pas &#234;tre prot&#233;g&#233; avec des LinkDemands | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2142"
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# CA2142&#160;: Le code transparent ne doit pas &#234;tre prot&#233;g&#233; avec des LinkDemands
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2142|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode transparente requiert un <xref:System.Security.Permissions.SecurityAction> ou une autre demande de sécurité.  
  
## Description de la règle  
 Cette règle se déclenche sur les méthodes transparentes qui requièrent l'accès de LinkDemands.  Le code transparent de sécurité ne doit pas être responsable de la vérification de la sécurité d'une opération. Par conséquent, il ne doit pas demander d'autorisations.  Étant donné que les méthodes transparentes sont supposées être neutre de sécurité, elles ne doivent pas prendre de décisions de sécurité.  En outre, le code critique sécurisé, qui prend des décisions de sécurité ne doit pas compter sur du code transparent pour avoir pris une telle décision précédemment.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, supprimez la demande de liaison sur la méthode transparente ou marquez la méthode avec l'attribut <xref:System.Security.SecuritySafeCriticalAttribute> si elle exécute des vérifications de sécurité, telles que les demandes de sécurité.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 Dans l'exemple suivant, la règle déclenche la méthode parce que la méthode est transparente et est marquée avec un LinkDemand <xref:System.Security.PermissionSet> qui contient un <xref:System.Security.Permissions.SecurityAction>.  
  
 [!code-cs[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]  
  
 Ne supprimez aucun avertissement de cette règle.