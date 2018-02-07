---
title: "Implémenter une interface - génération de code (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 990f87cd0f1abf9d4f62ecd321ef038d689b75f4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2018
---
# <a name="implement-an-interface-in-visual-basic"></a>Implémenter une interface dans Visual Basic
**Quoi :** vous permet de générer immédiatement le code requis pour implémenter une interface. 

**Quand :** vous voulez hériter d’une interface.  

**Pourquoi :** vous pouvez implémenter manuellement tous les éléments d’une interface un par un, mais cette fonctionnalité générera automatiquement toutes les signatures de la méthode. 

**Comment :**

1. Placez votre curseur sur la ligne ondulée rouge indiquant que vous avez référencé une interface, mais que vous n’avez pas implémenté tous les membres requis.

   ![Code mis en surbrillance](media/interface-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Implémenter une interface (explicitement)** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Implémenter l'interface explicitement** dans la fenêtre contextuelle d’aperçu.
     * Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![Ampoule](media/bulb-vb.png) qui apparaît.
     * Cliquez sur le bouton ![Ampoule](media/bulb-vb.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

   ![Implémenter un aperçu de classe](media/interface-preview-vb.png)

   >[!TIP]
   >Utilisez le lien [**Aperçu des modifications**](../../ide/preview-changes.md) en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.
   >
   >Vous pouvez utiliser les liens **Document**, **Projet** et **Solution** en bas de la fenêtre d’aperçu pour créer les signatures de méthode appropriées sur plusieurs classes qui implémentent l’interface.

1. Les signatures de la méthode de l’interface seront créées automatiquement, prêtes à être implémentées.

   ![Résultat de l’action Implémenter une classe](media/interface-result-vb.png)

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)