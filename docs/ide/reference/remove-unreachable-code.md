---
title: Supprimer le code inaccessible dans Visual Studio (refactorisation)
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1e5bdab773cf70963e1d0f485a7779e57084c8a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655602"
---
# <a name="remove-unreachable-code-refactoring"></a>Supprimer le code inaccessible dans Visual Studio (refactorisation)

Cette refactorisation s’applique à :

- C#

**Quoi :** supprime le code qui ne sera jamais exécuté.

**Quand :** votre programme ne dispose d’aucun chemin d’accès à un extrait de code, rendant cet extrait de code inutile.

**Pourquoi :** pour améliorer la lisibilité et la maintenance en supprimant un code superflu et qui ne sera jamais exécuté.

## <a name="how-to"></a>Procédure

1. Placez votre curseur n’importe où dans le code en grisé qui n’est pas accessible :

![Code inaccessible en grisé](media/unreachablecode-faded-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl**+ **.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Supprimer le code inaccessible** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
      - Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Supprimer le code inaccessible** dans la fenêtre contextuelle d’aperçu.

1. Lorsque vous êtes satisfait de la modification, appuyez sur **Entrée** ou cliquez sur le correctif dans le menu pour valider les modifications.

Exemple :

```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)