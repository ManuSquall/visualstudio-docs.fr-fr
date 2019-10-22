---
title: Déplacer la déclaration de variable près de la référence
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c0a82b48a556e26866393661d4b87836db765abb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666497"
---
# <a name="move-declaration-near-reference-refactoring"></a>Déplacer la déclaration près de la référence (refactorisation)

Cette refactorisation s’applique à :

- C#

**Quoi :** vous permet de déplacer des déclarations de variables plus près de leur utilisation.

**Quand :** vous avez des déclarations de variables qui peuvent être plus proches.

**Pourquoi :** vous pouvez laisser la déclaration telle quelle, mais cela peut provoquer des problèmes de lisibilité ou de masquage des informations. Vous pouvez tenter une refactorisation pour améliorer la lisibilité.

## <a name="how-to"></a>Procédure

1. Placez votre curseur dans la déclaration de variable.

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer la déclaration près de la référence** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
      - Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer la déclaration près de la référence** dans la fenêtre contextuelle d’aperçu.

1. Lorsque vous êtes satisfait de la modification, appuyez sur **Entrée** ou cliquez sur le correctif dans le menu pour valider les modifications.

Exemple :

```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)