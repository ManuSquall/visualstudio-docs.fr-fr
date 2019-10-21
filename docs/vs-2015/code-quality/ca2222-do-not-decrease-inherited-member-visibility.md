---
title: 'Ca2222 : ne réduisez pas la visibilité des membres hérités | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3dda56e6980133b0e33893fbb814c4a3a7008c49
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656058"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222 : Ne réduisez pas la visibilité des membres hérités
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Category|Microsoft. usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode privée dans un type non scellé a une signature qui est identique à une méthode publique déclarée dans un type de base. La méthode privée n’est pas finale.

## <a name="rule-description"></a>Description de la règle
 Vous ne devez pas modifier le modificateur d’accès destiné aux membres hérités. La modification d'un membre hérité au profit d'un état privé n'empêche pas les appelants d'accéder à l'implémentation de classe de base de la méthode. Si le membre est rendu privé et que le type est non scellé, les types qui héritent peuvent appeler la dernière implémentation publique de la méthode dans la hiérarchie d’héritage. Si vous devez modifier le modificateur d’accès, la méthode doit être marquée comme finale ou son type doit être sealed pour empêcher la méthode d’être substituée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez l’accès pour qu’il soit non privé. Si votre langage de programmation le prend en charge, vous pouvez également rendre la méthode finale.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole cette règle.

 [!code-csharp[FxCop.Usage.InheritedPublic#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InheritedPublic#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/vb/FxCop.Usage.InheritedPublic.vb#1)]
