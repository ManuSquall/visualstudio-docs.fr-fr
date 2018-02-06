---
title: "Introduire une variable locale - génération de code (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 6ba9478c09e55df54f94ed93c7a694f798ae76b4
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="introduce-a-local-variable-in-c"></a>Introduire une variable locale en C# #

**Quoi :** vous permet de générer immédiatement une variable locale pour remplacer une expression existante.

**Quand :** vous disposez d’un code pouvant être facilement réutilisé ultérieurement s’il figurait dans une variable locale.

**Pourquoi :** vous pourriez copier et coller le code plusieurs fois pour l’utiliser dans différents emplacements, mais il est préférable d’effectuer l’opération une fois, d’enregistrer le résultat dans une variable locale puis d’utiliser la variable locale de manière globale.

**Comment :**

1. Mettez en surbrillance l’expression que vous souhaitez assigner à une nouvelle variable locale.

   ![Code mis en surbrillance](media/local-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations** puis sélectionnez **Introduire un élément local pour toutes les occurrences de) '*expression*'** dans la fenêtre contextuelle d’aperçu, où *expression* est le code que vous avez mis en surbrillance.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations** puis sélectionnez **Introduire un élément local pour toutes les occurrences de) '*expression*'** dans la fenêtre contextuelle d’aperçu, où *expression* est le code que vous avez mis en surbrillance.
     * Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

   ![Introduire un aperçu local](media/local-preview-cs.png)

   > [!TIP]
   > Utilisez le lien [**Aperçu des modifications**](../../ide/preview-changes.md) en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.

1. La variable locale sera créée automatiquement avec le type déduit de son utilisation.  Renommez la nouvelle variable locale.

   ![Résultat de l’action Introduire une valeur locale](media/local-result-cs.png)

   > [!NOTE]
   > Vous pouvez utiliser l’option de menu **.. toutes les occurrences de...**  pour remplacer chaque instance de l’expression sélectionnée trouvée, et pas seulement celle que vous avez spécifiquement mise en surbrillance.

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)
