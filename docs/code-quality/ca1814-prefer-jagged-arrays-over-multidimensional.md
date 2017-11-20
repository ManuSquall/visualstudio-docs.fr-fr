---
title: "CA1814 : Préférez tableaux en escalier multidimensionnels | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa1420ab01426cbfeaaf5d70238df19fde50ea9a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814 : Utilisez des tableaux en escalier à la place de tableaux multidimensionnels
|||  
|-|-|  
|TypeName|PreferJaggedArraysOverMultidimensional|  
|CheckId|CA1814|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un membre est déclaré comme un tableau multidimensionnel.  
  
## <a name="rule-description"></a>Description de la règle  
 Un tableau en escalier est un tableau dont les éléments sont des tableaux. Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui conduit à un gaspillage d'espace plus restreint pour certains groupes de données.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, changez le tableau multidimensionnel en tableau en escalier.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Supprimer un avertissement de cette règle si le tableau multidimensionnel ne gaspille pas d’espace.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre des déclarations de tableaux en escalier et multidimensionnels.  
  
 [!code-vb[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/VisualBasic/ca1814-prefer-jagged-arrays-over-multidimensional_1.vb)]
 [!code-csharp[FxCop.Performance.JaggedArrays#1](../code-quality/codesnippet/CSharp/ca1814-prefer-jagged-arrays-over-multidimensional_1.cs)]