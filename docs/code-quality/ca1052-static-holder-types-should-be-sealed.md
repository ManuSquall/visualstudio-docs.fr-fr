---
title: 'CA1052 : Les types de conteneurs statiques doivent être sealed | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- StaticHolderTypesShouldBeSealed
- CA1052
helpviewer_keywords:
- CA1052
- StaticHolderTypesShouldBeSealed
ms.assetid: 51a3165d-781e-4a55-aa0d-ea25fee7d4f2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6fc3954c4c446ff578790e92bc60dd97e42a0d8c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1052-static-holder-types-should-be-sealed"></a>CA1052 : Les types de conteneurs statiques doivent être sealed
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldBeSealed|  
|CheckId|CA1052|  
|Category|Microsoft.Design|  
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
