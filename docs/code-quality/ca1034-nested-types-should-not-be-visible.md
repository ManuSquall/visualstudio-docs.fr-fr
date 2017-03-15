---
title: "CA1034&#160;: Les types imbriqu&#233;s ne doivent pas &#234;tre visibles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
helpviewer_keywords: 
  - "NestedTypesShouldNotBeVisible"
  - "CA1034"
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1034&#160;: Les types imbriqu&#233;s ne doivent pas &#234;tre visibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NestedTypesShouldNotBeVisible|  
|CheckId|CA1034|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type visible de l'extérieur contient une déclaration d'un type visible de l'extérieur.  Les énumérations imbriquées et les types protégés sont exemptés de cette règle.  
  
## Description de la règle  
 Un type imbriqué représente un type déclaré dans la portée d'un autre type.  Les types imbriqués sont utiles pour encapsuler les détails de l'implémentation privée du type conteneur.  Utilisés à cette fin, les types imbriqués ne doivent pas être visibles de l'extérieur.  
  
 N'utilisez pas de types imbriqués visibles de l'extérieur pour le regroupement logique ou pour éviter des collisions de noms ; utilisez plutôt des espaces de noms.  
  
 Les types imbriqués incluent la notion d'accessibilité des membres, que quelques programmeurs ne comprennent pas clairement.  
  
 Les types protégés peuvent être utilisés dans les sous\-classes et les types imbriqués dans des scénarios de personnalisation avancée.  
  
## Comment corriger les violations  
 Si vous ne souhaitez pas que le type imbriqué soit visible de l'extérieur, modifiez l'accessibilité du type.  Sinon, éliminez le type imbriqué de son parent.  Si le but de l'imbrication consiste à catégoriser le type imbriqué, utilisez plutôt un espace de noms pour créer une hiérarchie.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 L'exemple suivant présente un type qui enfreint la règle.  
  
 [!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
 [!code-cs[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
 [!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]