---
title: Supprimer le code inaccessible dans Visual Studio (refactorisation) | Microsoft Docs
ms.custom: ''
ms.date: 01/26/2018
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: douge
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 2c4e142582e4ee3a3e0308c5368c58fac79f8c6f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
     - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Supprimer le code inaccessible** dans la fenêtre contextuelle d’aperçu.
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