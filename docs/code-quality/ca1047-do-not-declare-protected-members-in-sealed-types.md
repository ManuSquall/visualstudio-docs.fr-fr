---
title: "CA1047&#160;: Ne pas d&#233;clarer les membres prot&#233;g&#233;s dans les types sealed | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDeclareProtectedMembersInSealedTypes"
  - "CA1047"
helpviewer_keywords: 
  - "CA1047"
  - "DoNotDeclareProtectedMembersInSealedTypes"
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1047&#160;: Ne pas d&#233;clarer les membres prot&#233;g&#233;s dans les types sealed
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|  
|CheckId|CA1047|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un type public est `sealed` \(`NotInheritable` en Visual basic\) et déclare un membre protégé ou un type imbriqué protégé.  Cette règle ne rapporte pas de violations pour les méthodes <xref:System.Object.Finalize%2A> qui doivent suivre ce schéma.  
  
## Description de la règle  
 Les types déclarent des membres protégés afin que des types qui héritent puissent accéder au membre ou le substituer.  Par définition, vous ne pouvez pas hériter d'un type sealed \(scellé\) ; en d'autres termes, les méthodes protégées sur les types sealed ne peuvent pas être appelées.  
  
 Le compilateur C\# émet un avertissement pour cette erreur.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, changez le niveau d'accès du membre en privé ou rendez le type héritable.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  Laisser le type dans son état actuel peut induire des problèmes de maintenance et ne fournit aucun avantage.  
  
## Exemple  
 L'exemple suivant affiche un type qui ne respecte pas cette règle.  
  
 [!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
 [!code-cs[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]