---
title: Supprimer le code inaccessible dans Visual Studio (refactorisation)
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: douge
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 73b04dafc094e05c57c626333a1d614de3ba76a1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945673"
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