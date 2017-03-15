---
title: "CA2222&#160;: Ne r&#233;duisez pas la visibilit&#233; des membres h&#233;rit&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotDecreaseInheritedMemberVisibility"
  - "CA2222"
helpviewer_keywords: 
  - "CA2222"
  - "DoNotDecreaseInheritedMemberVisibility"
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2222&#160;: Ne r&#233;duisez pas la visibilit&#233; des membres h&#233;rit&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode privée dans un type non\-sealed \(non scellé\) présente une signature identique à une méthode publique déclarée dans un type de base.  La méthode privée n'est pas finale.  
  
## Description de la règle  
 Vous ne devez pas modifier le modificateur d'accès destiné aux membres hérités.  La modification d'un membre hérité au profit d'un état privé n'empêche pas les appelants d'accéder à l'implémentation de classe de base de la méthode.  Si le membre est rendu privé et si le type est non\-sealed \(non scellé\), hériter des types peut entraîner l'appel à la dernière implémentation publique de la méthode au sein de la hiérarchie d'héritage.  Si vous devez changer le modificateur d'accès, la méthode doit être marquée comme finale ou son type doit être sealed \(scellé\) pour empêcher la substitution de la méthode.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez l'accès pour lui attribuer l'état non privé.  Vous pouvez également rendre la méthode finale si votre langage de programmation le permet.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant affiche un type qui ne respecte pas cette règle.  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-cs[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]