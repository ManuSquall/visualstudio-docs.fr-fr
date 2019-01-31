---
title: Renommer un nom de fichier pour qu’il corresponde à un type
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4625d8c4b6bce3235fe07682cb6a0e977258adf6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948178"
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-refactoring"></a>Synchroniser un type avec un nom de fichier ou un nom de fichier avec un type (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** Vous permet de renommer un type pour qu’il corresponde au nom de fichier, ou de renommer un nom de fichier afin qu’il corresponde au type qu’il contient.

**Quand :** Vous avez renommé un fichier ou un type et n’avez pas encore mis à jour le fichier ou type correspondant.

**Pourquoi :** Si vous placez un type dans un fichier avec un autre nom, ou vice versa, il est difficile de trouver ce que vous cherchez. En renommant le type ou le nom de fichier, le code devient plus lisible, ce qui facilite la navigation.

## <a name="how-to"></a>Procédure

1. Mettez en surbrillance ou placez le curseur de texte dans le nom du type à synchroniser :

   - C# :

       ![Code mis en surbrillance (C#)](media/synctype-highlight-cs.png)

   - Visual Basic :

       ![Code mis en surbrillance (Visual Basic)](media/synctype-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Renommer le fichier en *TypeName*.cs** dans la fenêtre contextuelle d’aperçu, où *TypeName* est le nom du type que vous avez sélectionné.
      - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Renommer le type en _Filename_.vb** dans la fenêtre contextuelle d’aperçu, où *Filename* est le nom du fichier actuel.
   - **Souris**
      - Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Renommer le fichier en *TypeName*.cs** dans la fenêtre contextuelle d’aperçu, où *TypeName* est le nom du type que vous avez sélectionné.
      - Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Renommer le type en _Filename_.vb** dans la fenêtre contextuelle d’aperçu, où *Filename* est le nom du fichier actuel.

   Le type ou le fichier est renommé.

   - C# : Dans l’exemple ci-dessous, le fichier **MyClass.cs** a été renommé **MyNewClass.cs** afin de correspondre au nom du type.

       ![Résultat de l’action Inclure (C#)](media/synctype-result-cs.png)

   - Visual Basic : Dans l’exemple ci-dessous, le fichier **Employee.vb** a été renommé **Person.vb** afin de correspondre au nom du type.

       ![Résultat de l’action Inclure (Visual Basic)](media/synctype-result-vb.png)

> REMARQUE : Cette refactorisation n’est pas encore disponible pour les projets .NET Standard et .NET Core.

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
