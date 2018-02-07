---
title: "Implémenter une classe abstraite - génération de code (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cfed7f-f090-4369-8a85-2dcd4c7cf12b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: f089ffbe33d4a36e84d6d39abb3b3db3c4b2aeb7
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2018
---
# <a name="implement-an-abstract-class-in-c"></a>Implémenter une classe abstraite en C# #
**Quoi :** vous permet de générer immédiatement le code requis pour implémenter une classe abstraite. 

**Quand :** vous voulez hériter d’une classe abstraite.  

**Pourquoi :** vous pouvez implémenter manuellement tous les membres abstraits un par un, mais cette fonctionnalité générera automatiquement toutes les signatures de la méthode. 

**Comment :**

1. Placez votre curseur sur la ligne ondulée rouge indiquant que vous avez hérité d’une classe abstraite, mais que vous n’avez pas implémenté tous les membres requis.

   ![Code mis en surbrillance](media/abstract-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Implémenter une classe abstraite** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Implémenter une classe abstraite** dans la fenêtre contextuelle d’aperçu.
     * Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![Ampoule](media/bulb-cs.png) qui apparaît.
     * Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

   ![Implémenter un aperçu de classe](media/abstract-preview-cs.png)

   >[!TIP]
   >Utilisez le lien [**Aperçu des modifications**](../../ide/preview-changes.md) en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.
   >
   >Vous pouvez utiliser les liens **Document**, **Projet** et **Solution** en bas de la fenêtre d’aperçu pour créer les signatures de méthode appropriées sur plusieurs classes qui héritent de la classe abstraite.

1. Les signatures de la méthode abstraite seront créées automatiquement, prêtes à être implémentées.

   ![Résultat de l’action Implémenter une classe](media/abstract-result-cs.png)

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)
