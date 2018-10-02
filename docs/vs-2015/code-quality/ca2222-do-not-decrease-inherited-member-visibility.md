---
title: 'CA2222 : Ne réduisez pas la visibilité des membres hérités | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9e631fc55a85e1d1a0383949d7e7592c6a5da44d
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589770"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222 : Ne réduisez pas la visibilité des membres hérités
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2222 : ne réduisez pas la visibilité des membres hérités](https://docs.microsoft.com/visualstudio/code-quality/ca2222-do-not-decrease-inherited-member-visibility).

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Category|Microsoft.Usage|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode privée dans un type unsealed a une signature qui est identique à une méthode publique déclarée dans un type de base. La méthode privée n’est pas finale.

## <a name="rule-description"></a>Description de la règle
 Vous ne devez pas modifier le modificateur d’accès destiné aux membres hérités. La modification d'un membre hérité au profit d'un état privé n'empêche pas les appelants d'accéder à l'implémentation de classe de base de la méthode. Si le membre est rendu privé et le type est non scellé, hériter de types permettre appeler la dernière implémentation publique de la méthode dans la hiérarchie d’héritage. Si vous devez modifier le modificateur d’accès, la méthode doit être marquée comme finale ou son type doit être sealed pour empêcher le remplacement de la méthode.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez l’accès pour être non privée. Vous pouvez également, si votre langage de programmation prend en charge, vous pouvez rendre la méthode finale.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant illustre un type qui enfreint cette règle.

 [!code-csharp[FxCop.Usage.InheritedPublic#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/cs/FxCop.Usage.InheritedPublic.cs#1)]
 [!code-vb[FxCop.Usage.InheritedPublic#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.InheritedPublic/vb/FxCop.Usage.InheritedPublic.vb#1)]



