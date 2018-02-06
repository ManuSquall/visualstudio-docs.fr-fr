---
title: "Implémenter une interface - génération de code (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebff2ad-25b6-4adc-8762-60d23bdd639a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 908e11da78b2a83fb3da23d28b5cc52613f7b0f2
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="implement-an-interface-in-c"></a>Implémenter une interface dans C# #
**Quoi :** vous permet de générer immédiatement le code requis pour implémenter une interface. 

**Quand :** vous voulez hériter d’une interface.  

**Pourquoi :** vous pouvez implémenter manuellement tous les éléments d’une interface un par un, mais cette fonctionnalité générera automatiquement toutes les signatures de la méthode. 

**Comment :**

1. Placez votre curseur sur la ligne ondulée rouge indiquant que vous avez référencé une interface, mais que vous n’avez pas implémenté tous les membres requis.

   ![Code mis en surbrillance](media/interface-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Implémenter une interface (explicitement)** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Implémenter l'interface explicitement** dans la fenêtre contextuelle d’aperçu.
     * Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![Ampoule](media/bulb-cs.png) qui apparaît.
     * Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

   ![Implémenter un aperçu de classe](media/interface-preview-cs.png)

   >[!TIP]
   >Utilisez le lien [**Aperçu des modifications**](../../ide/preview-changes.md) en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.
   >
   >Vous pouvez utiliser les liens **Document**, **Projet** et **Solution** en bas de la fenêtre d’aperçu pour créer les signatures de méthode appropriées sur plusieurs classes qui implémentent l’interface.

1. Les signatures de la méthode de l’interface seront créées automatiquement, prêtes à être implémentées.

   ![Résultat de l’action Implémenter une classe](media/interface-result-cs.png)

   >[!TIP]
   >Utilisez l’option **Implémenter l'interface explicitement** pour faire précéder chaque méthode générée du nom de l’interface et éviter ainsi les conflits de noms.
   >
   >![Résultat de l’action Implémenter l'interface explicitement](media/interface-explicitresult-cs.png); 

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)  
