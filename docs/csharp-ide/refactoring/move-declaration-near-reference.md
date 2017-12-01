---
title: "Déplacez la déclaration près de la référence - (refactorisation c#) | Documents Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: d79d55ae-f6bb-4902-8db2-e7fe01bdb0bf
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.openlocfilehash: f784ac9fec1dce1f21ba4b9f1f0e83b4b7deb001
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/29/2017
---
# <a name="move-declaration-near-reference-in-c"></a>Déplacez la déclaration près de la référence en c# #
**Ce que :** vous permet de déplacer les déclarations de variable de plus près à leur utilisation.

**Quand :** avoir de déclarations de variables qui peuvent être dans une portée plus restreinte.

**Pourquoi :** vous pouvez l’ignorer tel qu’il s’agit, mais qui peuvent provoquer des problèmes de lisibilité ou le masquage des informations. Il s’agit d’un risque pour la refactorisation pour améliorer la lisibilité.

**Comment faire :**

1. Placez votre curseur dans la déclaration de variable.

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **déplacer la déclaration près de la référence** à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Cliquez sur le code, sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **déplacer la déclaration près de la référence** à partir du message de fenêtre d’aperçu.

1. Lorsque vous êtes satisfait de la modification, appuyez sur **entrée** ou cliquez sur la correction dans le menu et les modifications seront validées.

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
[Refactorisation (C#)](../refactoring-csharp.md)  
[Aperçu des modifications](../../ide/preview-changes.md)