---
title: Inline variable temporaire - (refactorisation c#) | Documents Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0182179f-f74f-47a2-a1dc-b60c86f9abaf
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e6e9ed28a42aa3d7521a059b668eed8ae1d28b8e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="inline-a-temporary-variable-with-c"></a>Une variable temporaire en ligne avec c# #
**Ce que :** vous permet de supprimer l’utilisation d’une variable temporaire et remplacez-le par le code réel à la place.

**Quand :** l’utilisation de la variable temporaire rend le code plus difficile à comprendre.  

**Pourquoi :** suppression d’une variable temporaire peut rendre le code plus facile à lire dans certaines situations

**Comment faire :**

1. Mettez en surbrillance ou placez le curseur de texte à l’intérieur de la variable temporaire pour être inline :

   ![Code en surbrillance](media/inline_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **variable temporaire de Inline** à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Cliquez sur le code, sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **variable temporaire de Inline** à partir du message de fenêtre d’aperçu.

   La variable est supprimée et ses utilisations remplacé par la valeur de la variable immédiatement.

   ![Résultats inline](media/inline_result.png)

## <a name="see-also"></a>Voir aussi  
[Refactorisation (C#)](../refactoring-csharp.md)