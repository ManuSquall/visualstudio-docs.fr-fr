---
title: Remplacer une variable temporaire par sa valeur
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a7c691efcc507212aa0649b6c4b4179fb8288f06
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423168"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Inclure une variable temporaire (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** Vous permet de supprimer une variable temporaire et de la remplacer par sa valeur.

**Quand :** L’utilisation de la variable temporaire complique la lecture du code.

**Pourquoi :** La suppression d’une variable temporaire peut faciliter la lecture du code.

## <a name="how-to"></a>Procédure

1. Mettez en surbrillance ou placez le curseur dans la variable temporaire à inclure :

   - C# :

       ![Code mis en surbrillance (C#)](media/inline-highlight-cs.png)

   - Visual Basic :

       ![Code mis en surbrillance (Visual Basic)](media/inline-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit sur le code et sélectionnez le menu **Actions rapides et refactorisations**.

3. Sélectionnez **Inclure une variable temporaire** dans la fenêtre contextuelle d’aperçu.

   La variable est supprimée et ses utilisations sont remplacées par la valeur de la variable.

   - C# :

      ![Résultat de l’action Inclure (C#)](media/inline-result-cs.png)

   - Visual Basic :

      ![Résultat de l’action Inclure (Visual Basic)](media/inline-result-vb.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)