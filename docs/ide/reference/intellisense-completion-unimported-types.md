---
title: Autocomplétion IntelliSense pour les types non importés
description: Comment utiliser la saisie semi-automatique IntelliSense pour les types que vous n’avez pas encore importés avec une directive `using`.
ms.date: 06/20/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f313cfa8520e4c13b310be0f9223466c529ca18f
ms.sourcegitcommit: 16bcaca215de75479695738d3c2d703c78c3500e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/21/2019
ms.locfileid: "67312917"
---
# <a name="intellisense-completion-for-unimported-types"></a>Autocomplétion IntelliSense pour les types non importés

Cette refactorisation s’applique à :

- C#

**Quoi :** IntelliSense apporte l’autocomplétion pour les types non importés.

**Quand :** Vous souhaitez ajouter un type qui a déjà une dépendance dans votre projet, mais l’instruction d’importation n’a pas encore été ajoutée à votre fichier. 

**Pourquoi :** Vous n’avez pas besoin d’ajouter manuellement l’instruction d’importation à votre fichier.

## <a name="how-to"></a>Procédure

1. Une fois que vous commencez à utiliser un type qui a une dépendance dans votre projet, IntelliSense vous donnera des suggestions.
2. Appuyez sur la **touche de tabulation**. 

   L’instruction import est ajoutée à votre fichier.

   ![Autocomplétion IntelliSense pour les types non importés](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
