---
title: Remplacer une variable temporaire par sa valeur en C# | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 626224e8ed90196294f7b3ded245bb5272f70595
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2018
---
# <a name="inline-a-temporary-variable-with-c"></a>Inclure une variable temporaire avec C# #

**Quoi :** vous permet de supprimer une variable temporaire et de la remplacer par sa valeur.

**Quand :** l’utilisation de la variable temporaire complique la lecture du code.

**Pourquoi :** la suppression d’une variable temporaire peut faciliter la lecture du code.

**Comment :**

1. Mettez en surbrillance ou placez le curseur dans la variable temporaire à inclure :

   ![Code mis en surbrillance](media/inline-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**.
   * **Souris**
     * Cliquez avec le bouton droit sur le code et sélectionnez le menu **Actions rapides et refactorisations**.

1. Sélectionnez **Inclure une variable temporaire** dans la fenêtre contextuelle d’aperçu.

   La variable sera supprimée et ses utilisations seront aussitôt remplacées par la valeur de la variable.

   ![Résultat de l’action Inclure](media/inline-result-cs.png)

## <a name="see-also"></a>Voir aussi

[Refactorisation](../refactoring-in-visual-studio.md)