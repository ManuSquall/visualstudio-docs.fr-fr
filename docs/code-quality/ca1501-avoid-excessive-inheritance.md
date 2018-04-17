---
title: 'CA1501 : Éviter l’excès d’héritage | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b0f91c762a283f53970e600ff081ffa5e7b74298
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501 : Éviter l'excès d'héritage
|||  
|-|-|  
|TypeName|AvoidExcessiveInheritance|  
|CheckId|CA1501|  
|Category|Microsoft.Maintainability|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type est imbriqué de plus de quatre niveaux dans sa hiérarchie d'héritage.  
  
## <a name="rule-description"></a>Description de la règle  
 Les hiérarchies de type profondément imbriquées peuvent être difficiles à suivre, comprendre et gérer. Cette règle limite l’analyse aux hiérarchies dans le même module.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, dérivez le type d’un type de base qui est le moins profond dans la hiérarchie d’héritage ou supprimez certains des types de base intermédiaires.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle. Toutefois, le code peut être plus difficile à gérer. Notez que, en fonction de la visibilité des types de base, résolution des violations de cette règle peut créer des modifications avec rupture. Par exemple, la suppression des types de base publics est une modification avec rupture.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type qui enfreint la règle.  
  
 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]