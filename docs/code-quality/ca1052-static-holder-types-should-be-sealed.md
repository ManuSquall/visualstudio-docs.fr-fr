---
title: "CA1052 : Les types de conteneurs statiques doivent être sealed | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: deb02958ac89c350c4dc616b68693ee41b3019f5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052 : Les types de conteneurs statiques doivent être sealed
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|Catégorie|Microsoft.Design|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type public ou protégé contient uniquement des membres statiques et n’est pas déclaré avec le [sealed](/dotnet/csharp/language-reference/keywords/sealed) ([NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)) modificateur.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle suppose qu’un type qui contient uniquement des membres statiques n’est pas conçu pour être hérité, car le type ne fournit pas toutes les fonctionnalités qui peuvent être substituées dans un type dérivé. Un type qui n’est pas destiné à être hérité doit être marqué avec le `sealed` modificateur d’empêcher son utilisation comme type de base.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, marquez le type comme `sealed`. Si vous ciblez [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 ou version ultérieure, une meilleure approche consiste à marquer le type comme `static`. De cette manière, vous évitez d’avoir à déclarer un constructeur privé pour empêcher la création de la classe.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Supprimer un avertissement de cette règle uniquement si le type est conçu pour être héritée. L’absence de la `sealed` modificateur suggère que le type est utile en tant que type de base.  
  
## <a name="example-of-a-violation"></a>Exemple de Violation  
  
### <a name="description"></a>Description  
 L’exemple suivant montre un type qui enfreint la règle.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_1.cs)]
 [!code-vb[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/VisualBasic/ca1052-static-holder-types-should-be-sealed_1.vb)]
 [!code-cpp[FxCop.Design.StaticMembers#1](../code-quality/codesnippet/CPP/ca1052-static-holder-types-should-be-sealed_1.cpp)]  
  
## <a name="fix-with-the-static-modifier"></a>Résoudre avec le modificateur statique  
  
### <a name="description"></a>Description  
 L’exemple suivant montre comment la corriger une violation de cette règle en marquant le type avec la `static` modificateur.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Design.StaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1052-static-holder-types-should-be-sealed_2.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1053 : Les types de conteneurs statiques ne doivent pas comporter de constructeur](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)
