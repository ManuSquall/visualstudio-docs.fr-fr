---
title: "CA2146&#160;: Les types doivent &#234;tre au moins aussi critiques que les types de base et les interfaces | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2146"
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2146&#160;: Les types doivent &#234;tre au moins aussi critiques que les types de base et les interfaces
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|  
|CheckId|CA2146|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type transparent est dérivé d'un type marqué avec le <xref:System.Security.SecuritySafeCriticalAttribute> ou le <xref:System.Security.SecurityCriticalAttribute>, ou un type marqué avec l'attribut <xref:System.Security.SecuritySafeCriticalAttribute> est dérivé d'un type marqué avec l'attribut <xref:System.Security.SecurityCriticalAttribute>.  
  
## Description de la règle  
 Cette règle se déclenche lorsqu'un type dérivé a un attribut de transparence de sécurité qui n'est pas aussi critique que son type de base ou l'interface implémentée.  Seuls les types critiques peuvent dériver des types de base critiques ou implémenter des interfaces critiques, et seuls les types critiques ou critiques sécurisés peuvent dériver des types de base critiques sécurisés ou implémenter des interfaces critiques sécurisées.  Les violations de cette règle dans la transparence de niveau 2 provoquent une <xref:System.TypeLoadException> pour le type dérivé.  
  
## Comment corriger les violations  
 Pour résoudre cette violation, marquez le type dérivé ou d'implémentation avec un attribut de transparence qui est au moins aussi critique que l'interface ou le type de base.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 [!CODE [FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2146.typesmustbeatleastascriticalasbasetypes#1)]