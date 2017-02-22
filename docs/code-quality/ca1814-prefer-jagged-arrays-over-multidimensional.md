---
title: "CA1814&#160;: Utilisez des tableaux en escalier &#224; la place de tableaux multidimensionnels | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PreferJaggedArraysOverMultidimensional"
  - "CA1814"
helpviewer_keywords: 
  - "CA1814"
  - "PreferJaggedArraysOverMultidimensional"
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1814&#160;: Utilisez des tableaux en escalier &#224; la place de tableaux multidimensionnels
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PreferJaggedArraysOverMultidimensional|  
|CheckId|CA1814|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un membre est déclaré en tant que tableau multidimensionnel.  
  
## Description de la règle  
 Un tableau en escalier est un tableau dont les éléments sont des tableaux.  Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui conduit à un gaspillage d'espace plus restreint pour certains groupes de données.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, changez le tableau multidimensionnel en tableau en escalier.  
  
## Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle si le tableau multidimensionnel ne gaspille pas d'espace.  
  
## Exemple  
 L'exemple suivant présente des déclarations destinées à des tableaux en escalier et multidimensionnels.  
  
 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-cs[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]