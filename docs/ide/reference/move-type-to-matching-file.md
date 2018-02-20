---
title: "Déplacer un type vers un fichier correspondant dans Visual Studio (refactorisation) | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 62187c88fa2d2cf7ecf1b358fa0c03416be449a8
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Déplacer un type vers un fichier correspondant (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de déplacer le type sélectionné vers un fichier distinct portant le même nom.

**Quand :** vous avez plusieurs classes, structures, interfaces, etc. dans un même fichier et que vous souhaitez les séparer.

**Pourquoi :** placer plusieurs types dans un même fichier peut ralentir la recherche de ces types. En déplaçant les types vers des fichiers portant le même nom, le code devient plus lisible et cela facilite la navigation.

## <a name="how-to"></a>Procédure

1. Mettez en surbrillance ou placez le curseur de texte dans le nom du type à déplacer :

   - C# :

    ![Code mis en surbrillance (C#)](media/movetype-highlight-cs.png)

   - Visual Basic :

    ![Code mis en surbrillance (Visual Basic)](media/movetype-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
     - Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer le type vers *TypeName*.cs** dans la fenêtre contextuelle d’aperçu, où *TypeName* est le nom du type que vous avez sélectionné.
   - **Souris**
     - Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer le type vers *TypeName*.cs** dans la fenêtre contextuelle d’aperçu, où *TypeName* est le nom du type que vous avez sélectionné.

   Le type est déplacé vers un nouveau fichier portant ce nom dans le cadre de votre solution.

   - C# :

    ![Résultat de l’action Inclure (C#)](media/movetype-result-cs.png)

   - Visual Basic :

    ![Résultat de l’action Inclure (Visual Basic)](media/movetype-result-vb.png)

## <a name="see-also"></a>Voir aussi

[Refactorisation](../refactoring-in-visual-studio.md)