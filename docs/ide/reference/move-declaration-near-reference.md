---
title: Déplacer la déclaration de variable près de la référence
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour déplacer des déclarations de variables plus près de leur utilisation.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ce731da61c0c119869c1c1b85a87ebe44fabf273
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927923"
---
# <a name="move-declaration-near-reference-refactoring"></a>Déplacer la déclaration près de la référence (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de déplacer des déclarations de variables plus près de leur utilisation.

**Quand :** vous avez des déclarations de variables qui peuvent être plus proches.

**Pourquoi :** vous pouvez laisser la déclaration telle quelle, mais cela peut provoquer des problèmes de lisibilité ou de masquage des informations. Vous pouvez tenter une refactorisation pour améliorer la lisibilité.

## <a name="how-to"></a>Procédures

1. Placez votre curseur dans la déclaration de variable.

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer la déclaration près de la référence** dans la fenêtre contextuelle d’aperçu.
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
