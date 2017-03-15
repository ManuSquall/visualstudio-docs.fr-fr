---
title: "CA1048&#160;: Ne pas d&#233;clarer les membres virtuels dans les types sealed | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareVirtualMembersInSealedTypes"
  - "CA1048"
helpviewer_keywords: 
  - "CA1048"
  - "DoNotDeclareVirtualMembersInSealedTypes"
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA1048&#160;: Ne pas d&#233;clarer les membres virtuels dans les types sealed
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|  
|CheckId|CA1048|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type public est sealed \(scellé\) et déclare une méthode qui est à la fois `virtual` \(`Overridable` en Visual Basic\) et non finale.  Cette règle ne rapporte pas de violations pour les types délégués qui doivent suivre ce schéma.  
  
## Description de la règle  
 Les types déclarent des méthodes comme étant virtuelles afin d'hériter de types en mesure de substituer l'implémentation de la méthode virtuelle.  Par définition, vous ne pouvez pas hériter d'un type sealed, et retirer ainsi toute signification à une méthode virtuelle sur un type sealed.  
  
 Les compilateurs Visual Basic .NET et C\# ne permettent pas aux types de violer cette règle.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, rendez la méthode non virtuelle ou le type héritable.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Laisser le type dans son état actuel peut induire des problèmes de maintenance et ne fournit aucun avantage.  
  
## Exemple  
 L'exemple suivant affiche un type qui ne respecte pas cette règle.  
  
 [!CODE [FxCop.Design.SealedVirtual#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Design.SealedVirtual#1)]