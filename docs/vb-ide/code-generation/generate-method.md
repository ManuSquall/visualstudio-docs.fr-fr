---
title: "Générer une méthode - génération de Code (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8505f9a4fa8571e0e1c1e45f092d1b0e40c8ee9b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-method-in-visual-basic"></a>Générer une méthode dans Visual Basic
**Ce que :** vous permet d’ajouter immédiatement une méthode à une classe. 

**Quand :** vous introduire une nouvelle méthode et que vous souhaitez correctement la déclarer, automatiquement.  

**Pourquoi :** vous pouviez déclarer la méthode et les paramètres avant de l’utiliser, mais cette fonctionnalité génère automatiquement la déclaration. 

**Comment faire :**

1. Placez votre curseur sur la ligne où il existe une ligne ondulée rouge, indiquant que vous avez utilisé une méthode qui n’existe pas encore.

   ![Code en surbrillance](media/method_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **générer une méthode** à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Avec le bouton droit et sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **générer une méthode** à partir du message de fenêtre d’aperçu.
     * Placez le curseur sur la ligne ondulée rouge et cliquez sur le ![Ampoule](media/bulb.png) icône qui s’affiche.
     * Cliquez sur le bouton ![Ampoule](media/bulb.png) icône qui apparaît dans la marge de gauche, si le curseur de texte se trouve déjà sur la ligne de la ligne ondulée rouge.

   ![Génération d’un aperçu de méthode](media/method_preview.png)

   >[!TIP]
   >Utilisez le [ **aperçu des modifications** ](../../ide/preview-changes.md) lien en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.

1. La méthode est créée automatiquement avec des paramètres à partir de son utilisation.

   ![Générer le résultat de la méthode](media/method_result.png)
  
## <a name="see-also"></a>Voir aussi  
[Génération de code (Visual Basic)](../code-generation-vb.md)  
[Aperçu des modifications](../../ide/preview-changes.md)