---
title: Déplacer un type vers un espace de noms
ms.date: 06/17/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 821e915a0b66f25c5b89a83b31e93b01aea6f400
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "67292710"
---
# <a name="move-type-to-namespace"></a>Déplacer un type vers un espace de noms

Cette refactorisation s’applique à :

- C#

**Quoi :** Déplacez type dans l’espace de nom.

**Quand :** Vous voulez déplacer un type vers un autre namespace ou dossier. 

**Pourquoi:** Vous souhaitez refactorer des parties de votre solution et avoir un moyen rapide de déplacer un type vers un espace de nom ou un dossier différent. 

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans le nom de la classe.
2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
3. Sélectionnez **Déplacer vers l’espace de noms**.

   ![Refactorisation avec Déplacer vers l’espace de noms](media/move-to-namespace.png)

4. Dans la boîte de dialogue qui s’ouvre, sélectionnez l’espace de noms cible vers lequel vous souhaitez déplacer le type. 

   ![Sélectionner une boîte de dialogue d’espace de noms](media/select-target-namespace.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
