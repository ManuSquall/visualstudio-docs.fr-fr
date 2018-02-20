---
title: "Extraire une méthode dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4ccdab053e06efc11b6f9c42d391d4b4fc1f85f7
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="extract-a-method-refactoring"></a>Extraire une méthode (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de transformer un fragment de code dans sa propre méthode.

**Quand :** vous avez un fragment de code existant dans une méthode qui doit être appelée à partir d’une autre méthode.

**Pourquoi :** vous pouvez copier/coller ce code, mais cela entraîne une duplication. Une meilleure solution consiste à refactoriser ce fragment dans sa propre méthode pouvant être appelée librement par toute autre méthode.

## <a name="how-to"></a>Procédure

1. Mettez en surbrillance le code à extraire :

   - C# :

    ![Code mis en surbrillance (C#)](media/extractmethod-highlight-cs.png)

   - Visual Basic :

    ![Code mis en surbrillance (Visual Basic)](media/extractmethod-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
     - Appuyez sur **Ctrl+R**, puis **Ctrl+M**. (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
     - Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire la méthode** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
     - Sélectionnez **Modifier > Refactoriser > Extraire la méthode**.
     - Cliquez avec le bouton droit sur le code, puis sélectionnez **Refactoriser > Extraire > Extraire la méthode**.
     - Cliquez avec le bouton droit sur le code et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire la méthode** dans la fenêtre contextuelle d’aperçu.

   La méthode sera immédiatement créée. À partir d’ici, il vous suffit de taper le nouveau nom de la méthode pour la renommer.

   > [!TIP]
   > Vous pouvez également mettre à jour les commentaires et autres chaînes afin d’utiliser ce nouveau nom, et [afficher un aperçu des modifications](../../ide/preview-changes.md) avant de les enregistrer, à l’aide des cases à cocher de la boîte de dialogue **Renommer** qui apparaît en haut à droite de votre IDE.

   - C# :
   
    ![Renommer la méthode (C#)](media/extractmethod-rename-cs.png)

   - Visual Basic :
   
    ![Renommer la méthode (Visual Basic)](media/extractmethod-rename-vb.png)

1. Quand vous êtes satisfait du changement, appuyez sur le bouton **Appliquer** ou sur la touche **Entrée** pour valider les changements.

## <a name="see-also"></a>Voir aussi

[Refactorisation](../refactoring-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)