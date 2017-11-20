---
title: "CA2222 : Ne réduisez pas la visibilité des membres hérités | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 520882b8d1b24cc7bc346ae185de8f186e4fa163
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222 : Ne réduisez pas la visibilité des membres hérités
|||  
|-|-|  
|TypeName|DoNotDecreaseInheritedMemberVisibility|  
|CheckId|CA2222|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode privée dans un type unsealed possède une signature qui est identique à une méthode publique déclarée dans un type de base. La méthode privée n’est pas finale.  
  
## <a name="rule-description"></a>Description de la règle  
 Vous ne devez pas modifier le modificateur d'accès destiné aux membres hérités. La modification d'un membre hérité au profit d'un état privé n'empêche pas les appelants d'accéder à l'implémentation de classe de base de la méthode. Si le membre est rendu privé et le type est non scellé, hériter des types peut appeler la dernière implémentation publique de la méthode dans la hiérarchie d’héritage. Si vous devez modifier le modificateur d’accès, la méthode doit être marquée comme finale, ou son type doit être sealed pour empêcher le remplacement de la méthode.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, modifiez l’accès pour être non privée. Ou bien, si votre langage de programmation prend en charge, vous pouvez rendre la méthode finale.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type qui viole cette règle.  
  
 [!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
 [!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]