---
title: "CA2134&#160;: La transparence des m&#233;thodes doit rester coh&#233;rente lors de la substitution de m&#233;thodes de base | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2134"
ms.assetid: 3b17e487-0326-442e-90e1-dc0ba9cdd3f2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2134&#160;: La transparence des m&#233;thodes doit rester coh&#233;rente lors de la substitution de m&#233;thodes de base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MethodsMustOverrideWithConsistentTransparency|  
|CheckId|CA2134|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Cette règle se déclenche lorsqu'une méthode marquée avec l' <xref:System.Security.SecurityCriticalAttribute> substitue une méthode qui est transparente ou marquée avec l' <xref:System.Security.SecuritySafeCriticalAttribute>.  La règle se déclenche également lorsqu'une méthode transparente ou marquée avec <xref:System.Security.SecuritySafeCriticalAttribute> se substitue à une méthode marquée avec <xref:System.Security.SecurityCriticalAttribute>.  
  
 La règle est appliquée lors de la substitution d'une méthode virtuelle ou de l'implémentation d'une interface.  
  
## Description de la règle  
 Cette règle déclenche sur les tentatives de modification de l'accessibilité à la sécurité d'une méthode située plus haut dans la chaîne d'héritage.  Par exemple, si une méthode virtuelle dans une classe de base est transparente ou critique sécurisée, alors, la classe dérivée doit la substituer par une méthode transparente ou sécurisée critique.  Inversement, si le virtuel est critique de sécurité, la classe dérivée doit le substituer avec une méthode critique de sécurité.  La même règle s'applique pour l'implémentation des méthodes d'interface.  
  
 Les règles de transparence sont mises en vigueur lorsque le code est compilé par le JIT et non au moment de l'exécution, afin que le calcul de transparence n'ait pas d'informations de type dynamique.  Par conséquent, le résultat du calcul de transparence doit pouvoir être déterminé uniquement à partir des types statiques qui sont compilés par le JIT, indépendamment du type dynamique.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, modifiez la transparence de la méthode qui remplace une méthode virtuelle ou implémente une interface pour restituer la transparence de la méthode virtuelle ou d'interface.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Les violations de cette règle provoquent une <xref:System.TypeLoadException> runtime pour les assemblys qui utilisent la transparence de niveau 2.  
  
## Exemples  
  
### Code  
 [!CODE [FxCop.Security.CA2134.MethodsMustOverrideWithConsistentTransparency#1](../CodeSnippet/VS_Snippets_CodeAnalysis/fxcop.security.ca2134.methodsmustoverridewithconsistenttransparency#1)]  
  
## Voir aussi  
 [Code transparent de sécurité, niveau 2](../Topic/Security-Transparent%20Code,%20Level%202.md)