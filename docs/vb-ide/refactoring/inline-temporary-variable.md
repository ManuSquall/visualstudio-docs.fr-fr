---
title: Variable temporaire inline - refactorisation (Visual Basic) | Documents Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a63d6407-5acb-4d5f-8c0e-ecedddc07177
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3607e646f5f1ccc6121e5ee8a5b71772008f1ce8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="inline-a-temporary-variable-in-visual-basic"></a>Inline, une variable temporaire en Visual Basic
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
[Refactorisation (Visual Basic)](../refactoring-vb.md)