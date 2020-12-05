---
title: Remonter des membres
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour extraire les membres jusqu’au type de base.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 159608644cb641aa2c84e4d55e92156215069030
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616874"
---
# <a name="pull-members-up"></a>Remonter des membres

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Ce qui suit :** Permet d’extraire les membres jusqu’au type de base.

Dans les **cas suivants :** Vous avez implémenté une interface et vous souhaitez déplacer un membre vers le type de base.

**Pourquoi :** L’extraction de membres permet à d’autres implémentations de votre interface d’hériter également de ces membres.

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans un membre d’une interface implémentée.
2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

   ![Remonter des membres](media/pull-members-up.png)

2. Sélectionnez **Remonter les membres vers le type de base**.

3. Dans la boîte de dialogue, sélectionnez les membres que vous souhaitez ajouter à l’interface sélectionnée.

   ![Remonter un membre](media/pull-members-up-dialog.png)

4. Choisissez **OK**. Les membres sélectionnés sont remontés dans l’interface.

   ![Membre remonté](media/pull-members-up-completed.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
