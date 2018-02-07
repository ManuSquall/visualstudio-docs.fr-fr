---
title: "Déplacer la déclaration de variable près de la référence en C# | Microsoft Docs"
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
ms.openlocfilehash: f61fbdc8dd24bb07082081557c875e9149c1c398
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2018
---
# <a name="move-declaration-near-reference-in-c"></a>Déplacer la déclaration près de la référence en C# #

**Quoi :** vous permet de déplacer des déclarations de variables plus près de leur utilisation.

**Quand :** vous avez des déclarations de variables qui peuvent être plus proches.

**Pourquoi :** vous pouvez laisser la déclaration telle quelle, mais cela peut provoquer des problèmes de lisibilité ou de masquage des informations. Vous pouvez tenter une refactorisation pour améliorer la lisibilité.

**Comment :**

1. Placez votre curseur dans la déclaration de variable.

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer la déclaration près de la référence** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer la déclaration près de la référence** dans la fenêtre contextuelle d’aperçu.

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

[Refactorisation](../refactoring-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)