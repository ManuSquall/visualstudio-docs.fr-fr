---
title: "CA2123 : Les demandes de liaison de substitution doivent &#234;tre identiques au composant de base | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
helpviewer_keywords: 
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2123 : Les demandes de liaison de substitution doivent &#234;tre identiques au composant de base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode publique ou protégée dans un type public substitue une méthode ou implémente une interface, et n'a pas le même [Demandes de liaison](../Topic/Link%20Demands.md) que l'interface ou la méthode virtuelle.  
  
## Description de la règle  
 Cette règle met en correspondance une méthode et sa méthode de base, qui est soit une interface, soit une méthode virtuelle dans un autre type, puis compare les demandes de liaison sur chacune.  Une violation est rapportée si la méthode ou la méthode de base affiche une demande de liaison et l'autre non.  
  
 Si cette règle est violée, un appelant malveillant peut contourner la demande de liaison simplement en appelant la méthode non protégée.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, appliquez la même demande de liaison à la méthode ou implémentation override.  Si ce n'est pas possible, marquez la méthode avec une demande complète ou supprimez l'attribut entièrement.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente différentes violations de cette règle.  
  
 [!code-cs[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## Voir aussi  
 [Instructions de codage sécurisé](../Topic/Secure%20Coding%20Guidelines.md)   
 [Demandes de liaison](../Topic/Link%20Demands.md)