---
title: Extraire une méthode
description: Transformez un fragment de code en sa propre méthode en sélectionnant le code et en tapant Ctrl+R, Ctrl+M.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 21f6ac868268c40ea6df837596546f86fd9a3a44
ms.sourcegitcommit: cd7f122c6850cf442a4ca42d51d05c7a8fe9038d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98129469"
---
# <a name="extract-a-method-refactoring"></a>Extraire une méthode (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de transformer un fragment de code dans sa propre méthode.

**Quand :** vous avez un fragment de code existant dans une méthode qui doit être appelée à partir d’une autre méthode.

**Pourquoi :** vous pouvez copier/coller ce code, mais cela entraîne une duplication. Une meilleure solution consiste à refactoriser ce fragment dans sa propre méthode pouvant être appelée librement par toute autre méthode.

## <a name="how-to"></a>Procédures

1. Mettez en surbrillance le code à extraire :

   - C# :

       ! Capture d’écran montrant le code C# de la classe Program. Dans la fonction main de cette classe, une ligne de code est mise en surbrillance.] (média/extractmethod-highlight-cs.png)

   - Visual Basic :

       ![Capture d’écran montrant Visual Basic code pour le Sub principal. Dans ce Sub, une ligne de code est mise en surbrillance.](media/extractmethod-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl+R**, puis **Ctrl+M**. (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
      - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire la méthode** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
      - Sélectionnez **Modifier > Refactoriser > Extraire la méthode**.
      - Cliquez avec le bouton droit sur le code, puis sélectionnez **Refactoriser > Extraire > Extraire la méthode**.
      - Cliquez avec le bouton droit sur le code et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire la méthode** dans la fenêtre contextuelle d’aperçu.

   La méthode sera immédiatement créée. À partir d’ici, il vous suffit de taper le nouveau nom de la méthode pour la renommer.

   > [!TIP]
   > Vous pouvez aussi mettre à jour les commentaires et d’autres chaînes pour utiliser ce nouveau nom, et [afficher un aperçu des changements](../../ide/preview-changes.md) avant de les enregistrer, à l’aide des cases à cocher de la boîte de dialogue **Renommer** qui apparaît en haut à droite de votre IDE.

   - C# :

      ![Capture d’écran montrant le code C# de la classe Program. Un nom de méthode est mis en surbrillance et la fenêtre contextuelle de renommage est ouverte.](media/extractmethod-rename-cs.png)

   - Visual Basic :

      ![Capture d’écran montrant Visual Basic code pour le Sub principal. Un nom de méthode est mis en surbrillance et la fenêtre contextuelle de renommage est ouverte.](media/extractmethod-rename-vb.png)

3. Quand vous êtes satisfait du changement, appuyez sur le bouton **Appliquer** ou sur la touche **Entrée** pour valider les changements.

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
