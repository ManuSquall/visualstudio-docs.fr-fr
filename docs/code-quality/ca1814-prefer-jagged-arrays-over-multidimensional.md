---
title: 'CA1814 : Préférez tableaux en escalier multidimensionnels | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f87c0141b437cebce2531b5b1ec4cd983fa1822
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814 : Utilisez des tableaux en escalier à la place de tableaux multidimensionnels
|||  
|-|-|  
|TypeName|PreferJaggedArraysOverMultidimensional|  
|CheckId|CA1814|  
|Category|Microsoft.Performance|  
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