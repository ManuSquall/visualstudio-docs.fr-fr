---
title: Remonter des membres
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2d1f7deb7aca1fed7b75b66b17ce2e4d63768a0d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969162"
---
# <a name="pull-members-up"></a>Remonter des membres

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** Permet de tirer les membres jusqu’au type de base.

**Quand :** Vous avez implémenté une interface et vous souhaitez déplacer un membre vers le type de base.

**Pourquoi:** Tirer les membres vers le haut permet à d’autres implémentations de votre interface d’hériter de ces membres ainsi.

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans un membre d’une interface implémentée.
2. Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Remonter des membres](media/pull-members-up.png)

2. Sélectionnez **Remonter les membres vers le type de base**.

3. Dans la boîte de dialogue, sélectionnez les membres que vous souhaitez ajouter à l’interface sélectionnée.

   ![Remonter un membre](media/pull-members-up-dialog.png)

4. Choisissez **OK**. Les membres sélectionnés sont remontés dans l’interface.

   ![Membre remonté](media/pull-members-up-completed.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
