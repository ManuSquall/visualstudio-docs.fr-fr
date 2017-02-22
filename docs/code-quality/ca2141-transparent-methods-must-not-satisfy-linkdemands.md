---
title: "CA2141&#160;: Les m&#233;thodes transparentes ne r&#233;pondent pas aux LinkDemands | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2141"
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2141&#160;: Les m&#233;thodes transparentes ne r&#233;pondent pas aux LinkDemands
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode transparente de sécurité appelle une méthode dans un assembly qui n'est pas marqué avec l'attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\), ou une méthode transparente de sécurité satisfait un <xref:System.Security.Permissions.SecurityAction>`.LinkDemand` pour un type ou une méthode.  
  
## Description de la règle  
 Répondre à un LinkDemand est une opération relative à la sécurité qui peut entraîner une élévation des privilèges accidentelle.  Le code transparent de sécurité ne doit pas répondre aux LinkDemands car il n'est pas soumis aux mêmes exigences d'audit de sécurité que le code critique de sécurité.  Les méthodes transparentes dans des assemblys de règles de sécurité de niveau 1 provoqueront la conversion de tous les LinkDemands qu'ils satisfont en demandes complètes au moment de l'exécution, ce qui peut provoquer des problèmes de performances.  Dans les assemblys de niveau 2 de l'ensemble de règles de sécurité, les méthodes transparentes ne pourront pas être compilées dans le compilateur juste\-à\-temps \(JIT\) si elles essaient de satisfaire un LinkDemand.  
  
 Dans les assemblys de niveau 2 de sécurité, les tentatives par une méthode transparente de sécurité pour satisfaire un LinkDemand ou appeler une méthode dans un assembly non\-APTCA déclenche un <xref:System.MethodAccessException> ; dans les assemblys de niveau 1 le LinkDemand devient une demande complète.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, marquez la méthode d'accès avec l'attribut <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> ou supprimez le LinkDemand de la méthode accédée.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 Dans cet exemple, une méthode transparente essaie d'appeler une méthode qui a un LinkDemand.  Cette règle déclenchera sur ce code.  
  
 [!code-cs[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]