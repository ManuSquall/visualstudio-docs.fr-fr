---
title: "Supprimer la refactorisation d’un code inaccessible pour C# dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs:
- csharp
ms.workload:
- dotnet
ms.openlocfilehash: 12b6910aad6399b72b3e4bc10e6b857cc98c09bb
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2018
---
# <a name="remove-unreachable-code-in-c"></a>Supprimer un code inaccessible en C# #

**Quoi :** supprime le code qui ne sera jamais exécuté.

**Quand :** votre programme ne dispose d’aucun chemin d’accès à un extrait de code, rendant cet extrait de code inutile.

**Pourquoi :** pour améliorer la lisibilité et la maintenance en supprimant un code superflu et qui ne sera jamais exécuté.

**Comment :**

1. Placez votre curseur n’importe où dans le code en grisé qui n’est pas accessible :

![Code inaccessible en grisé](media/unreachablecode-faded-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Supprimer le code inaccessible** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Supprimer le code inaccessible** dans la fenêtre contextuelle d’aperçu.

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

[Refactorisation](../refactoring-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)