---
title: 'CA1052 : Types de conteneurs statiques doivent être sealed | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d973d7ff5464b76228e917c83b3e62116e115718
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65693801"
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052 : Les types de conteneurs statiques doivent être sealed
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|StaticHolderTypesShouldBeSealed|
|CheckId|CA1052|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé contient uniquement des membres statiques et n’est pas déclaré avec le [sealed](https://msdn.microsoft.com/library/8e4ed5d3-10be-47db-9488-0da2008e6f3f) ([NotInheritable](https://msdn.microsoft.com/library/5c4da7c9-9562-4653-a947-1972e992f9f9)) modificateur.

## <a name="rule-description"></a>Description de la règle
 Cette règle suppose qu’un type qui contient uniquement des membres statiques n’est pas conçu pour être héritée, de le, car le type ne fournit pas toutes les fonctionnalités qui peuvent être substituées dans un type dérivé. Un type qui n’est pas destiné à être hérité doit être marqué avec le `sealed` modificateur d’empêcher son utilisation comme un type de base.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, marquez le type comme `sealed`. Si vous ciblez [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 ou une version antérieure, une meilleure approche consiste à marquer le type comme `static`. De cette manière, vous évitez d’avoir à déclarer un constructeur privé pour empêcher la création de la classe.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle uniquement si le type est conçu pour être hérité. L’absence de la `sealed` modificateur suggère que le type est utile comme type de base.

## <a name="example-of-a-violation"></a>Exemple de Violation

### <a name="description"></a>Description
 L’exemple suivant montre un type qui viole la règle.

### <a name="code"></a>Code
 [!code-cpp[FxCop.Design.StaticMembers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cpp/FxCop.Design.StaticMembers.cpp#1)]
 [!code-csharp[FxCop.Design.StaticMembers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/cs/FxCop.Design.StaticMembers.cs#1)]
 [!code-vb[FxCop.Design.StaticMembers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembers/vb/FxCop.Design.StaticMembers.vb#1)]

## <a name="fix-with-the-static-modifier"></a>Résoudre avec le modificateur Static

### <a name="description"></a>Description
 L’exemple suivant montre comment la corriger une violation de cette règle en marquant le type avec le `static` modificateur.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.StaticMembersFixed/cs/FxCop.Design.StaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1053 : Types de conteneurs statiques ne doivent pas avoir de constructeurs](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
