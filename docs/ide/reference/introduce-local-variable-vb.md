---
title: "Introduire une variable locale - génération de code (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1490d6ac-ed56-4d03-95db-c23f23cba70d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: abc0ef3ffdbada86a66bac9823894ee83d04047f
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2018
---
# <a name="introduce-a-local-variable-in-visual-basic"></a>Introduire une variable locale en Visual Basic
**Quoi :** vous permet de générer immédiatement une variable locale pour remplacer une expression existante.

**Quand :** vous disposez d’un code pouvant être facilement réutilisé ultérieurement s’il figurait dans une variable locale.  

**Pourquoi :** vous pourriez copier et coller le code plusieurs fois pour l’utiliser dans différents emplacements, mais il est préférable d’effectuer l’opération une fois, d’enregistrer le résultat dans une variable locale puis d’utiliser la variable locale de manière globale. 

**Comment :**

1. Mettez en surbrillance l’expression que vous souhaitez assigner à une nouvelle variable locale.

   ![Code mis en surbrillance](media/local-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations** puis sélectionnez **Introduire un élément local pour toutes les occurrences de) '*expression*'** dans la fenêtre contextuelle d’aperçu, où *expression* est le code que vous avez mis en surbrillance.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations** puis sélectionnez **Introduire un élément local pour toutes les occurrences de) '*expression*'** dans la fenêtre contextuelle d’aperçu, où *expression* est le code que vous avez mis en surbrillance.
     * Cliquez sur le bouton ![Ampoule](media/bulb-vb.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

   ![Introduire un aperçu local](media/local-preview-vb.png)

   >[!TIP]
   >Utilisez le lien [**Aperçu des modifications**](../../ide/preview-changes.md) en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.

1. La variable locale sera créée automatiquement avec le type déduit de son utilisation.  Renommez la nouvelle variable locale.

   ![Résultat de l’action Introduire une valeur locale](media/local-result-vb.png)

   >[!NOTE]
   >Vous pouvez utiliser l’option de menu **.. toutes les occurrences de...**  pour remplacer chaque instance de l’expression sélectionnée trouvée, et pas seulement celle que vous avez spécifiquement mise en surbrillance.

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md) 