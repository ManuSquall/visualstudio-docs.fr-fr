---
title: Rendre le membre statique
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1ecc66cb58ad11bd431acb341dae0493ce8192da
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77515301"
---
# <a name="make-member-static"></a>Rendre le membre statique

Cette refactorisation s’applique à :

- C#

**Quoi :** Rendre un membre statique.

**Quand :** Vous voulez qu’un membre non statique soit statique.

**Pourquoi:** Les membres statiques améliorent la lisibilité : savoir que le code spécifique est isolé facilite la compréhension, la reliure et la réutilisation. 

## <a name="how-to"></a>Procédures

1. Placez votre caret sur le nom du membre.

2. Appuyez **sur Ctrl**+**.** (période) pour déclencher le menu **Actions rapides et Refactorings.**

   ![Rendre le membre statique](media/make-member-static.png)

3. Sélectionnez **Rendre statique**.

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
