---
title: Extraire une méthode
description: Transformez un fragment de code en sa propre méthode en sélectionnant le code et en tapant Ctrl+R, Ctrl+M.
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a764fd0d95696866e914ec76a560a49d641acb47
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483672"
---
# <a name="extract-a-method-refactoring"></a>Extraire une méthode (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** Vous permet de transformer un fragment de code dans sa propre méthode.

**Quand :** Vous avez un fragment de code existant dans une méthode qui doit être appelée à partir d’une autre méthode.

**Pourquoi :** Vous pouvez copier/coller ce code, mais cela entraîne une duplication. Une meilleure solution consiste à refactoriser ce fragment dans sa propre méthode pouvant être appelée librement par toute autre méthode.

## <a name="how-to"></a>Procédure

1. Mettez en surbrillance le code à extraire :

   - C# :

       ![Code mis en surbrillance (C#)](media/extractmethod-highlight-cs.png)

   - Visual Basic :

       ![Code mis en surbrillance (Visual Basic)](media/extractmethod-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl+R**, puis **Ctrl+M**. (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
      - Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire la méthode** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
      - Sélectionnez **Modifier > Refactoriser > Extraire la méthode**.
      - Cliquez avec le bouton droit sur le code, puis sélectionnez **Refactoriser > Extraire > Extraire la méthode**.
      - Cliquez avec le bouton droit sur le code et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire la méthode** dans la fenêtre contextuelle d’aperçu.

   La méthode sera immédiatement créée. À partir d’ici, il vous suffit de taper le nouveau nom de la méthode pour la renommer.

   > [!TIP]
   > Vous pouvez aussi mettre à jour les commentaires et d’autres chaînes pour utiliser ce nouveau nom, et [afficher un aperçu des changements](../../ide/preview-changes.md) avant de les enregistrer, à l’aide des cases à cocher de la boîte de dialogue **Renommer** qui apparaît en haut à droite de votre IDE.

   - C# :

      ![Renommer la méthode (C#)](media/extractmethod-rename-cs.png)

   - Visual Basic :

      ![Renommer la méthode (Visual Basic)](media/extractmethod-rename-vb.png)

3. Quand vous êtes satisfait du changement, appuyez sur le bouton **Appliquer** ou sur la touche **Entrée** pour valider les changements.

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)