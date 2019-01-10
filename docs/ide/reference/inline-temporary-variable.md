---
title: Remplacer une variable temporaire par sa valeur
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: aa329dd3fe7d01046c35be9829aed4ca4519c3e1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909032"
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