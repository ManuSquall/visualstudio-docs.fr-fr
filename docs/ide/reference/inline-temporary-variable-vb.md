---
title: Remplacer une variable temporaire par sa valeur dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7553a67892322a1acb2db33d7a16b399b6f0b23a
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="inline-a-temporary-variable-in-visual-basic"></a>Inclure une variable temporaire dans Visual Studio

**Quoi :** vous permet de supprimer une variable temporaire et de la remplacer par sa valeur.

**Quand :** l’utilisation de la variable temporaire complique la lecture du code.

**Pourquoi :** la suppression d’une variable temporaire peut faciliter la lecture du code.

**Comment :**

1. Mettez en surbrillance ou placez le curseur dans la variable temporaire à inclure :

   ![Code mis en surbrillance](media/inline-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**.
   * **Souris**
     * Cliquez avec le bouton droit sur le code et sélectionnez le menu **Actions rapides et refactorisations**.

1. Sélectionnez **Inclure une variable temporaire** dans la fenêtre contextuelle d’aperçu.

   La variable sera supprimée et ses utilisations seront aussitôt remplacées par la valeur de la variable.

   ![Résultat de l’action Inclure](media/inline-result-vb.png)

## <a name="see-also"></a>Voir aussi

[Refactorisation](../refactoring-in-visual-studio.md)