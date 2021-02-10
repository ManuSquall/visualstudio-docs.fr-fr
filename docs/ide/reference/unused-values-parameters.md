---
title: Valeurs et paramètres inutilisés
description: En savoir plus sur les affectations de valeurs, les variables et les paramètres inutilisés et leur mode d’affichage dans l’éditeur de code dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/15/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cd0b6e936f4478cb4b74a3f004e69d77dbad7fbc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960609"
---
# <a name="unused-value-assignments-variables-and-parameters"></a>Affectations, variables et paramètres de valeur inutilisés

Cette refactorisation s’applique à :

- C#
- Visual Basic

**Ce qui suit :** Atténue les paramètres inutilisés et génère un avertissement pour les valeurs d’expression inutilisées. Le compilateur effectue également une analyse des flux pour rechercher les affectations de valeurs inutilisées. Les affectations de valeurs inutilisées apparaissent estompées et une ampoule s’affiche avec une [Action rapide](../quick-actions.md) pour supprimer l’affectation redondante. Les variables inutilisées avec des valeurs inconnues montrent une suggestion d’[Action rapide](../quick-actions.md) d’utiliser des [éléments ignorés](/dotnet/csharp/discards) à la place. (Les éléments ignorés sont des variables temporaires factices, qui sont inutilisées de façon intentionnelle dans le code d’une application. Ils peuvent réduire l’allocation mémoire et rendre votre code plus facile à lire.)

Dans les **cas suivants :** Vous avez des affectations de valeur, des paramètres ou des valeurs d’expression qui ne sont jamais utilisés.

**Pourquoi :** Il est parfois difficile de savoir si une assignation de valeur, une variable ou un paramètre n’est plus utilisé. Pour vous aider à repérer le code que vous pouvez supprimer, ces valeurs sont estompées ou génèrent un avertissement.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnostic des valeurs d’expression et des paramètres non utilisés

1. Avoir une affectation de valeur, une variable ou un paramètre qui n’est pas utilisé.
2. L’assignation de valeur ou le paramètre inutilisé apparaît en fondu. La valeur de l’expression inutilisée génère un avertissement.

  ![Paramètre inutilisé](media/unused-parameter.png)
  ![Valeur inutilisée](media/unused-value.png)
  ![Affectation de valeur inutilisée](media/unused-value-assignment.png)
  ![Élément ignoré de valeur inutilisée](media/unused-value-discard.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../csharp-developer-productivity.md)
