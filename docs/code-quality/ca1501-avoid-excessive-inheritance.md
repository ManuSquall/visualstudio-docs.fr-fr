---
title: "CA1501&#160;: &#201;viter l&#39;exc&#232;s d&#39;h&#233;ritage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1501"
  - "AvoidExcessiveInheritance"
helpviewer_keywords: 
  - "AvoidExcessiveInheritance"
  - "CA1501"
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1501&#160;: &#201;viter l&#39;exc&#232;s d&#39;h&#233;ritage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveInheritance|  
|CheckId|CA1501|  
|Catégorie|Microsoft.Maintainability|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type est imbriqué de plus de quatre niveaux dans sa hiérarchie d'héritage.  
  
## Description de la règle  
 Les hiérarchies de type profondément imbriquées peuvent être difficiles à suivre, comprendre et gérer.  Cette règle limite l'analyse aux hiérarchies contenues dans le même module.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, dérivez le type d'un type de base moins imbriqué dans la hiérarchie d'héritage ou supprimez certains des types de base intermédiaires.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle.  Cependant, il pourrait être plus difficile de gérer le code.  Notez qu'en fonction de la visibilité des types de base, la résolution des violations de cette règle peut créer des modifications avec rupture.  Par exemple, la suppression des types de base publics est une modification avec rupture.  
  
## Exemple  
 L'exemple suivant présente un type qui enfreint la règle.  
  
 [!code-cs[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]