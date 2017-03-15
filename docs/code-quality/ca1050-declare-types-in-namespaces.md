---
title: "CA1050&#160;: D&#233;clarer les types dans des espaces de noms | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
helpviewer_keywords: 
  - "CA1050"
  - "DeclareTypesInNamespaces"
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1050&#160;: D&#233;clarer les types dans des espaces de noms
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DeclareTypesInNamespaces|  
|CheckId|CA1050|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type public ou protégé est défini hors de la portée d'un espace de noms nommé.  
  
## Description de la règle  
 Les types sont déclarés dans les espaces de noms pour empêcher des collisions de dénomination, ainsi qu'en guise que méthode d'organisation de types connexes au sein d'une hiérarchie d'objets.  Les types situés hors de tout espace de noms nommé s'inscrivent dans un espace de noms global qui ne peut pas être référencé dans un code.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, placez le type dans un espace de noms.  
  
## Quand supprimer les avertissements  
 Même s'il n'est jamais nécessaire de supprimer un avertissement de cette règle, il est possible de le faire sans risque dans les cas où l'assembly ne sera jamais utilisé avec d'autres assemblys.  
  
## Exemple  
 L'exemple suivant présente une bibliothèque dotée d'un type déclaré incorrectement hors d'un espace de noms, et d'un autre de même nom, déclaré dans un espace de noms.  
  
 [!code-cs[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/CSharp/ca1050-declare-types-in-namespaces_1.cs)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../code-quality/codesnippet/VisualBasic/ca1050-declare-types-in-namespaces_1.vb)]  
  
## Exemple  
 L'application suivante utilise la bibliothèque définie précédemment.  Remarquez que le type déclaré hors d'un espace de noms est créé lorsque le nom `Test` n'est qualifié par aucun espace de noms.  Remarquez également que pour accéder au type `Test` dans `Goodspace`, le nom de l'espace de noms est requis.  
  
 [!CODE [FxCop.Design.TestTypesLive#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive#1)]