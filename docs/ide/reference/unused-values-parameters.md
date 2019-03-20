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
ms.openlocfilehash: afcf85fff188853890b86cf7deb13b2457f5e0b8
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157696"
---
# <a name="unused-expression-values-and-parameters"></a>Valeurs d’expression et paramètres inutilisés

Cette refactorisation s’applique à :

- C#
- Visual Basic

**Quoi :** Estompe les paramètres non utilisés et génère un avertissement pour les valeurs d’expression non utilisées.

**Quand :** Vous avez des paramètres ou des valeurs d’expression qui ne sont jamais utilisés.

**Pourquoi :** Il est parfois difficile de savoir si une valeur ou un paramètre n’est plus utilisé. Pour vous aider à repérer le code que vous pouvez supprimer, ces valeurs sont estompées ou génèrent un avertissement.

## <a name="unused-expression-values-and-parameters-diagnostic"></a>Diagnostic des valeurs d’expression et des paramètres non utilisés

1. Faites en sorte d’avoir une valeur d’expression ou un paramètre qui n’est pas utilisé.
2. Le paramètre inutilisé est estompé. La valeur d’expression inutilisée génère un avertissement.

  ![Paramètre inutilisé](media/unused-parameter.png)
  ![Valeur inutilisée](media/unused-value.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Conseils pour les développeurs .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
