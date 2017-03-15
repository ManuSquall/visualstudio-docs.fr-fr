---
title: "CA2122 : N&#39;exposez pas indirectement des m&#233;thodes avec des demandes de liaison | Microsoft Docs"
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
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
helpviewer_keywords: 
  - "CA2122"
  - "DoNotIndirectlyExposeMethodsWithLinkDemands"
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2122 : N&#39;exposez pas indirectement des m&#233;thodes avec des demandes de liaison
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|  
|CheckId|CA2122|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un membre public ou protégé présente un [Demandes de liaison](../Topic/Link%20Demands.md) et est appelé par un membre qui ne procède à aucune vérification de la sécurité.  
  
## Description de la règle  
 Une demande de liaison vérifie uniquement les autorisations de l'appelant immédiat.  Si un membre `X` n'effectue aucune des demandes de sécurité de ses appelants, et appelle un code protégé par une demande de liaison, un appelant dépourvu de l'autorisation nécessaire peut utiliser `X` pour accéder au membre protégé.  
  
## Comment corriger les violations  
 Ajoutez une [Données et modélisation](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) de sécurité ou une demande de liaison au membre afin qu'il ne fournisse plus d'accès non sécurisé au membre protégé par demande de liaison.  
  
## Quand supprimer les avertissements  
 Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que votre code ne donne aux appelants aucun accès à des opérations ou des ressources susceptibles d'être utilisées de façon néfaste.  
  
## Exemple  
 Les exemples suivants présentent une bibliothèque qui viole la règle, et une application qui montre la faiblesse de la bibliothèque.  La bibliothèque exemple fournit deux méthodes qui, ensemble, violent la règle.  La méthode `EnvironmentSetting` est sécurisée par une demande de liaison pour un accès illimité aux variables d'environnement.  La méthode `DomainInformation` n'effectue aucune des demandes de sécurité de ses appelants avant d'appeler `EnvironmentSetting`.  
  
 [!code-cs[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]  
  
## Exemple  
 L'application suivante appelle le membre de bibliothèque non sécurisé.  
  
 [!code-cs[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]  
  
 Cet exemple génère la sortie suivante.  
  
  **Valeur de membre sans garantie : seattle.corp.contoso.com**   
## Voir aussi  
 [Instructions de codage sécurisé](../Topic/Secure%20Coding%20Guidelines.md)   
 [Demandes de liaison](../Topic/Link%20Demands.md)   
 [Données et modélisation](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)