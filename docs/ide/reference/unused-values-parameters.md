---
title: Valeurs et paramètres inutilisés
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce2b0f1e0c0db45c478c3917306683b314da0564
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531875"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Affectations, variables et paramètres de valeur inutilisés

Cette refactorisation s’applique à :

- C#
- Visual Basic

**Quoi :** Efface les paramètres inutilisés et génère un avertissement pour les valeurs d’expression inutilisées. Le compilateur effectue également une analyse des flux pour rechercher les affectations de valeurs inutilisées. Les affectations de valeurs inutilisées apparaissent estompées et une ampoule s’affiche avec une [Action rapide](../quick-actions.md) pour supprimer l’affectation redondante. Les variables inutilisées avec des valeurs inconnues montrent une suggestion d’[Action rapide](../quick-actions.md) d’utiliser des [éléments ignorés](/dotnet/csharp/discards) à la place. (Les éléments ignorés sont des variables temporaires factices, qui sont inutilisées de façon intentionnelle dans le code d’une application. Ils peuvent réduire l’allocation mémoire et rendre votre code plus facile à lire.)

**Quand :** Vous avez des affectations de valeur, des paramètres ou des valeurs d’expression qui ne sont jamais utilisées.

**Pourquoi:** Parfois, il est difficile de dire si une affectation de valeur, variable ou paramètre n’est plus utilisée. Pour vous aider à repérer le code que vous pouvez supprimer, ces valeurs sont estompées ou génèrent un avertissement.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnostic des valeurs d’expression et des paramètres non utilisés

1. Avoir une affectation de valeur, une variable ou un paramètre qui n’est pas utilisé.
2. L’affectation ou le paramètre de valeur inutilisé semble délavé. La valeur d’expression inutilisée génère un avertissement.

  ![Paramètre inutilisé](media/unused-parameter.png)
  ![Valeur inutilisée](media/unused-value.png)
  ![Affectation de valeur inutilisée](media/unused-value-assignment.png)
  ![Élément ignoré de valeur inutilisée](media/unused-value-discard.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)
