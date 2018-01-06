---
title: Supprimez le Code inaccessible - (refactorisation c#) | Documents Microsoft
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: e57db74ea431d9090df1dc34fd3cff3cf03dd475
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="remove-unreachable-code-in-c"></a>Supprimez le code inaccessible en c# #
**Ce que :** supprime le code qui ne sera jamais exécuté.

**Quand :** votre programme ne comporte aucun chemin d’accès à un extrait de code, rendant cet extrait de code inutile.

**Pourquoi :** améliorer la lisibilité et facilité de maintenance en supprimant le code qui est superflu et ne sera jamais exécutée.

**Comment faire :**

1. Placez votre curseur n’importe où dans le code de fondu out n’est pas accessible :

![Passé code inaccessible](media/unreachablecode_faded.png)  

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **supprimer le code inaccessible** à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Cliquez sur le code, sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **supprimer le code inaccessible** à partir du message de fenêtre d’aperçu.

1. Lorsque vous êtes satisfait de la modification, appuyez sur **entrée** ou cliquez sur la correction dans le menu et les modifications seront validées.

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
[Refactorisation (C#)](../refactoring-csharp.md)  
[Aperçu des modifications](../../ide/preview-changes.md)