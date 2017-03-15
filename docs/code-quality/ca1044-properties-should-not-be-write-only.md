---
title: "CA1044&#160;: Les propri&#233;t&#233;s ne doivent pas &#234;tre en &#233;criture seule | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PropertiesShouldNotBeWriteOnly"
  - "CA1044"
helpviewer_keywords: 
  - "CA1044"
  - "PropertiesShouldNotBeWriteOnly"
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1044&#160;: Les propri&#233;t&#233;s ne doivent pas &#234;tre en &#233;criture seule
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|Catégorie|Microsoft.CSharp|  
|Modification avec rupture|Oui|  
  
## Cause  
 La propriété publique ou protégée présente un accesseur set mais aucun accesseur get.  
  
## Description de la règle  
 Les accesseurs get fournissent l'accès en lecture à une propriété et les accesseurs set fournissent l'accès en écriture.  Bien qu'il soit acceptable et souvent nécessaire de disposer d'une propriété en lecture seule, les règles de conception interdisent l'utilisation de propriétés en écriture seule.  Cela est dû au fait que si vous laissez la possibilité à un utilisateur de définir une valeur et que vous empêchez cet 'utilisateur d'afficher la valeur, vous ne garantissez aucune sécurité.  De plus, sans accès en lecture, l'état des objets partagés ne peut s'afficher, ce qui limite leur utilité.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez un accesseur get à la propriété.  Si le comportement d'une propriété en écriture seule est nécessaire, vous pouvez également envisager de convertir cette propriété en méthode.  
  
## Quand supprimer les avertissements  
 Il est fortement recommandé de ne pas supprimer d'avertissement de cette règle.  
  
## Exemple  
 Dans l'exemple suivant, `BadClassWithWriteOnlyProperty` est un type doté d'une propriété en écriture seule.  `GoodClassWithReadWriteProperty` contient le code corrigé.  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-cs[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]