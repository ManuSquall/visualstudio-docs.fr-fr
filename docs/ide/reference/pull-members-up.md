---
title: Remonter des membres
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 65ce1b44063fd6152fc300e32e7dd075fa8afcbf
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335853"
---
# <a name="pull-members-up"></a>Remonter des membres

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** permet de remonter les membres vers le type de base.

**Quand :** vous avez implémenté une interface et souhaitez déplacer un membre vers le type de base.

**Pourquoi :** le fait de faire remonter des membres permet à d’autres implémentations de votre interface d’hériter de ces membres.

## <a name="how-to"></a>Procédure

1. Placez votre curseur dans un membre d’une interface implémentée.
2. Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Remonter des membres](media/pull-members-up.png)

2. Sélectionnez **Remonter les membres vers le type de base**.

3. Dans la boîte de dialogue, sélectionnez les membres que vous souhaitez ajouter à l’interface sélectionnée.

   ![Remonter un membre](media/pull-members-up-dialog.png)

4. Choisissez **OK**. Les membres sélectionnés sont remontés dans l’interface.

   ![Membre remonté](media/pull-members-up-completed.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
