---
title: Saisie semi-automatique des valeurs DateTime et TimeSpan via le menu IntelliSense
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: eaa8a344e46c031b37b52106ba9aef25dac59b0c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290340"
---
# <a name="datetime-and-timespan-completion-through-intellisense-menu"></a>Saisie semi-automatique des valeurs DateTime et TimeSpan via le menu IntelliSense

Cette refactorisation s’applique à :

- C#

**Ce qui suit :** Saisie semi-automatique des littéraux de chaîne DateTime et TimeSpan via le menu IntelliSense.

Dans les **cas suivants :** Vous souhaitez écrire des littéraux de chaîne DateTime et TimeSpan. IntelliSense vous offre une saisie semi-automatique de base et une explication de ce que signifient chacun des caractères. 

**Pourquoi :** La mémorisation des formats DateTime est difficile et IntelliSense peut vous aider à les écrire.

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans le littéral de chaîne DateTime ou TimeSpan.
2. Appuyez sur **CTRL** + **Space** pour déclencher le menu **IntelliSense** .
3. Sélectionnez le caractère que vous souhaitez ajouter.

   ![Saisie semi-automatique DateTime IntelliSense](media/datetime-completion.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
