---
title: Autocomplétion IntelliSense pour les types non importés
description: Comment utiliser la saisie semi-automatique IntelliSense pour les types que vous n’avez pas encore importés avec une directive `using`.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 04ea7c94d3dd24c1a511544adca9bfac3370cd71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094269"
---
# <a name="intellisense-completion-for-unimported-types"></a>Autocomplétion IntelliSense pour les types non importés

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** IntelliSense donne l’achèvement pour les types non-prisés.

**Quand :** Vous souhaitez ajouter un type qui a déjà une dépendance dans votre projet, mais l’état d’importation n’a pas encore été ajouté à votre fichier. 

**Pourquoi:** Vous n’avez pas à ajouter manuellement l’énoncé d’importation à votre fichier.

## <a name="how-to"></a>Procédures

1. Une fois que vous commencez à utiliser un type qui a une dépendance dans votre projet, IntelliSense vous donnera des suggestions.
2. Appuyez **sur Tab**. 

   L’instruction import est ajoutée à votre fichier.

   ![Autocomplétion IntelliSense pour les types non importés](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
