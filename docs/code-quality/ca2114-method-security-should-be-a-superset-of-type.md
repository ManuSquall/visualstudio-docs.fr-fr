---
title: "CA2114 :La s&#233;curit&#233; de la m&#233;thode doit &#234;tre un sur-ensemble du type | Microsoft Docs"
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
  - "MethodSecurityShouldBeASupersetOfType"
  - "CA2114"
helpviewer_keywords: 
  - "CA2114"
  - "MethodSecurityShouldBeASupersetOfType"
ms.assetid: 663f7aa4-8be5-4bd5-be92-4e9444f07077
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2114 :La s&#233;curit&#233; de la m&#233;thode doit &#234;tre un sur-ensemble du type
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MethodSecurityShouldBeASupersetOfType|  
|CheckId|CA2114|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type présente une sécurité déclarative, une de ses méthodes présente une sécurité déclarative pour la même action de sécurité, l'action de sécurité n'est pas [Demandes de liaison](../Topic/Link%20Demands.md) ou [Inheritance Demands](http://msdn.microsoft.com/fr-fr/28b9adbb-8f08-4f10-b856-dbf59eb932d9), et les autorisations vérifiées par le type ne constituent pas un sous\-ensemble des autorisations vérifiées par la méthode.  
  
## Description de la règle  
 Pour une même action, une méthode ne doit pas présenter de sécurité déclarative à la fois au niveau méthode et au niveau type.  Les deux contrôles ne sont pas combinés ; seule une demande de niveau méthode s'applique.  Par exemple, si un type demande une autorisation `X` et que l'une de ses méthodes demande une autorisation `Y`, le code n'a pas besoin de l'autorisation `X` pour exécuter la méthode.  
  
## Comment corriger les violations  
 Passez en revue votre code pour vous assurer que les deux actions sont requises.  Si les deux actions sont requises, assurez\-vous que l'action de niveau de méthode inclut la sécurité spécifiée au niveau type.  Par exemple, si votre type demande une autorisation `X`, et si sa méthode doit également demander une autorisation `Y`, la méthode doit demander explicitement `X` et `Y`.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si la méthode ne requiert pas la sécurité spécifiée par le type.  Toutefois, ce scénario n'est pas ordinaire et peut indiquer la nécessité d'un examen approfondi du design.  
  
## Exemple  
 L'exemple suivant utilise des autorisations d'environnement pour montrer les dangers liés à la violation de cette règle.  Dans cet exemple, le code d'application crée une instance du type sécurisé avant de refuser l'autorisation requise par le type.  Dans un scénario de menace réel, l'application impliquerait une autre manière d'obtenir une instance de l'objet.  
  
 Dans l'exemple suivant, la bibliothèque demande une autorisation d'écriture pour un type et une autorisation de lecture pour une méthode.  
  
 [!code-cs[FxCop.Security.MethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_1.cs)]  
  
## Exemple  
 Le code d'application suivant montre la vulnérabilité de la bibliothèque en appelant la méthode alors qu'il ne satisfait pas la configuration requise en matière de sécurité au niveau du type.  
  
 [!code-cs[FxCop.Security.TestMethodLevelSecurity#1](../code-quality/codesnippet/CSharp/ca2114-method-security-should-be-a-superset-of-type_2.cs)]  
  
 Cet exemple génère la sortie suivante.  
  
  **\[Toutes les autorisations\]Informations personnelles : 6\/16\/1964 12h \[Aucune autorisation d'écriture \(requise par le type\)\] Informations personnelles : 6\/16\/1964 12h00 \[Aucune autorisation de lecture \(requise par la méthode\)\] N'a pas pu accéder à des informations personnelles : La requête a échoué.**   
## Voir aussi  
 [Instructions de codage sécurisé](../Topic/Secure%20Coding%20Guidelines.md)   
 [Inheritance Demands](http://msdn.microsoft.com/fr-fr/28b9adbb-8f08-4f10-b856-dbf59eb932d9)   
 [Demandes de liaison](../Topic/Link%20Demands.md)   
 [Données et modélisation](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)