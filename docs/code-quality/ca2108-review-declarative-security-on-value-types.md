---
title: "CA2108&#160;: V&#233;rifiez la s&#233;curit&#233; d&#233;clarative dans les types valeur | Microsoft Docs"
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
  - "ReviewDeclarativeSecurityOnValueTypes"
  - "CA2108"
helpviewer_keywords: 
  - "CA2108"
  - "ReviewDeclarativeSecurityOnValueTypes"
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2108&#160;: V&#233;rifiez la s&#233;curit&#233; d&#233;clarative dans les types valeur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewDeclarativeSecurityOnValueTypes|  
|CheckId|CA2108|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type valeur public ou protégé est sécurisé par un [Données et modélisation](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) ou un [Demandes de liaison](../Topic/Link%20Demands.md).  
  
## Description de la règle  
 Les types valeur sont alloués et initialisés par leurs constructeurs par défaut avant que d'autres constructeurs s'exécutent.  Si un type valeur est sécurisé par une action Demand ou LinkDemand, et si l'appelant ne dispose pas des autorisations qui satisfont la vérification de sécurité, tout constructeur autre que le constructeur par défaut échoue, et une exception de sécurité est levée.  Le type valeur n'est pas libéré ; il est laissé dans l'état défini par son constructeur par défaut.  Ne comptez pas sur le fait qu'un appelant qui passe une instance du type valeur dispose automatiquement de l'autorisation de créer l'instance ou d'y accéder.  
  
## Comment corriger les violations  
 Vous ne pouvez pas corriger une violation de cette règle à moins de supprimer la vérification de sécurité à partir du type, et d'utiliser en lieu et place des vérifications de sécurité de niveau méthode.  Remarquez que ce mode de correction de la violation n'empêche pas des appelants dotés d'autorisations inadéquates d'obtenir des instances du type valeur.  Vous devez vous assurer qu'une instance du type valeur, dans son état par défaut, n'expose pas d'informations sensibles, et ne peut pas être utilisée de façon préjudiciable.  
  
## Quand supprimer les avertissements  
 Vous pouvez supprimer un avertissement de cette règle si un appelant peut obtenir des instances du type valeur dans son état par défaut sans que cela constitue une menace pour la sécurité.  
  
## Exemple  
 L'exemple suivant présente une bibliothèque qui contient un type valeur qui enfreint cette règle.  Remarquez que le type `StructureManager` suppose qu'un appelant qui passe une instance du type valeur dispose de l'autorisation de créer l'instance ou d'y accéder.  
  
 [!code-cs[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]  
  
## Exemple  
 L'application suivante montre la faiblesse de la bibliothèque.  
  
 [!code-cs[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]  
  
 Cet exemple génère la sortie suivante.  
  
  **Constructeur personnalisé de structure : Échec de la demande.**  
**Nouvelles valeurs SecuredTypeStructure 100 100**  
**Nouvelles valeurs SecuredTypeStructure 200 200**   
## Voir aussi  
 [Demandes de liaison](../Topic/Link%20Demands.md)   
 [Données et modélisation](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)