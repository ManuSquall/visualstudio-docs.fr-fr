---
title: Saisie semi-automatique des valeurs DateTime et TimeSpan via le menu IntelliSense
ms.date: 07/31/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 36b6d5440e532653845638f87f7f1d7066af6ba3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87471550"
---
# <a name="datetime-and-timespan-completion-through-intellisense-menu"></a>Saisie semi-automatique des valeurs DateTime et TimeSpan via le menu IntelliSense

Cette refactorisation s’applique à :

- C#

**Ce qui suit :** Littéral de chaîne DateTime et TimeSpan et saisie semi-automatique de la chaîne de format via le menu IntelliSense.

Dans les **cas suivants :** Vous souhaitez écrire un littéral de chaîne DateTime et TimeSpan et une chaîne de format. IntelliSense vous offre une saisie semi-automatique de base et une explication de ce que signifient chacun des caractères. 

**Pourquoi :** La mémorisation des formats DateTime est difficile et IntelliSense peut vous aider à les écrire.

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans la chaîne de format DateTime ou TimeSpan.
2. Appuyez sur **CTRL** + **Space** pour déclencher le menu **IntelliSense** .
3. Sélectionnez le caractère que vous souhaitez ajouter.

   ![Saisie semi-automatique DateTime IntelliSense](media/datetime-completion.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
