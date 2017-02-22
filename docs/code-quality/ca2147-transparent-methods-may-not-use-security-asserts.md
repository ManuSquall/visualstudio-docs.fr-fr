---
title: "CA2147&#160;: Les m&#233;thodes transparentes ne peuvent pas utiliser d&#39;assertions de s&#233;curit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SecurityTransparentCodeShouldNotAssert"
  - "CA2147"
  - "CA2128"
helpviewer_keywords: 
  - "CA2128"
  - "SecurityTransparentCodeShouldNotAssert"
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2147&#160;: Les m&#233;thodes transparentes ne peuvent pas utiliser d&#39;assertions de s&#233;curit&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecurityTransparentCodeShouldNotAssert|  
|CheckId|CA2147|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Aucune autorisation suffisante n'est accordée à un code marqué comme <xref:System.Security.SecurityTransparentAttribute> pour procéder à une assertion.  
  
## Description de la règle  
 Cette règle analyse toutes les méthodes et tous les types dans un assembly qui est entièrement transparent ou mi\-transparent et mi\-critique, et elle signale toutes les utilisations déclaratives ou impératives de <xref:System.Security.CodeAccessPermission.Assert%2A>.  
  
 Au moment de l'exécution, tous les appels à <xref:System.Security.CodeAccessPermission.Assert%2A> à partir d'un code transparent provoqueront la levée de <xref:System.InvalidOperationException>.  Cela peut se produire dans les assemblys entièrement transparents ainsi que dans les assemblys mi\-transparents et mi\-critiques, où une méthode ou un type est déclaré transparent, mais inclut une assertion déclarative ou impérative.  
  
 La version [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 a introduit une fonctionnalité appelée *transparence*.  Les méthodes, les champs, les interfaces, les classes et les types individuels peuvent être transparents ou critiques.  
  
 Le code transparent n'est pas autorisé à élever les privilèges de sécurité.  Par conséquent, toutes les autorisations accordées ou sollicitées sont automatiquement passées du code à l'appelant ou au domaine d'application d'hôte.  Les exemples d'élévations incluent les assertions, les LinkDemands, l'attribut SuppressUnmanagedCode et le code `unsafe`.  
  
## Comment corriger les violations  
 Pour résoudre le problème, marquez le code qui appelle l'assertion en tant que <xref:System.Security.SecurityCriticalAttribute> ou supprimez l'assertion.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun message de cette règle.  
  
## Exemple  
 Ce code échouera si `SecurityTestClass` est transparent, lorsque la méthode `Assert` lève une <xref:System.InvalidOperationException>.  
  
 [!CODE [FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2147.transparentmethodsmustnotusesecurityasserts#1)]  
  
## Exemple  
 Une option consiste à réviser le code de la méthode SecurityTransparentMethod comme dans l'exemple ci\-dessous, et si la méthode est considérée comme sans risque pour l'élévation, à la marquer comme critique sécurisée. Cela requiert qu'un audit de sécurité exempt d'erreurs, détaillé et exhaustif soit exécuté sur la méthode avec toutes les sorties d'appel qui se produisent dans cette dernière sous l'assertion :  
  
 [!CODE [FxCop.Security.SecurityTransparentCode2#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.SecurityTransparentCode2#1)]  
  
 Il est également possible de supprimer l'assertion du code et de permettre la transmission de toutes les demandes d'autorisation d'accès E\/S au fichier suivantes au\-delà de SecurityTransparentMethod par l'appelant.  Cela permet des vérifications de sécurité.  Dans ce cas, aucun audit de sécurité n'est habituellement nécessaire, car les demandes d'autorisation sont transmises à l'appelant et\/ou au domaine d'application.  Les demandes d'autorisation sont contrôlées attentivement au moyen de la stratégie de sécurité, de l'environnement d'hébergement et des autorisations liées à la source du code.  
  
## Voir aussi  
 [Avertissements liés à la sécurité](../code-quality/security-warnings.md)