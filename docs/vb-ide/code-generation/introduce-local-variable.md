---
title: "Introduire une variable locale - génération de Code (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1490d6ac-ed56-4d03-95db-c23f23cba70d
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 67302893dbebb65316b9c2aab09f70ddaa3e6567
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="introduce-a-local-variable-in-visual-basic"></a>Introduire une variable locale en Visual Basic
**Ce que :** vous permet de générer d’immédiatement une variable locale pour remplacer une expression existante.

**Quand :** vous disposez du code qui pourrait être facilement réutilisée ultérieurement si elle se trouvait dans une variable locale.  

**Pourquoi :** vous pourriez copier et coller le code plusieurs fois pour l’utiliser dans différents emplacements, mais il est préférable d’effectuer l’opération une fois, enregistre le résultat dans une variable locale et utiliser le throughought de variable locale. 

**Comment faire :**

1. Mettez en surbrillance l’expression que vous souhaitez affecter à une variable locale.

   ![Code en surbrillance](media/local_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez  **introduire un élément local (toutes les occurrences de) '*expression*' ** à partir de la fenêtre de la fenêtre Aperçu, où *expression* est le code que vous avez mis en surbrillance.
   * **Souris**
     * Avec le bouton droit et sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez  **introduire un élément local (toutes les occurrences de) '*expression*' ** à partir de la fenêtre de la fenêtre Aperçu, où *expression* est le code que vous avez mis en surbrillance.
     * Cliquez sur le bouton ![Ampoule](media/bulb.png) icône qui apparaît dans la marge de gauche, si le curseur de texte se trouve déjà sur la ligne de la ligne ondulée rouge.

   ![Introduire Aperçu local](media/local_preview.png)

   >[!TIP]
   >Utilisez le [ **aperçu des modifications** ](../../ide/preview-changes.md) lien en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.

1. La variable locale est créée automatiquement avec le type déduit à partir de son utilisation.  Donnez un nouveau nom à la nouvelle variable locale en le tapant.

   ![Présentez le résultat local](media/local_result.png)

   >[!NOTE]
   >Vous pouvez utiliser le **.. tous les occurrences de...**  option de menu pour remplacer chaque occurrence de l’expression sélectionnée trouvée, pas seulement celle que vous avez spécifiquement mis en surbrillance.

## <a name="see-also"></a>Voir aussi  
[Génération de code (Visual Basic)](../code-generation-vb.md)  
[Aperçu des modifications](../../ide/preview-changes.md) 