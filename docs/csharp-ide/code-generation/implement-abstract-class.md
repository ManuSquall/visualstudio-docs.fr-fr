---
title: "Implémenter une classe abstraite - génération de Code (c#) | Documents Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cfed7f-f090-4369-8a85-2dcd4c7cf12b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: ff462a62bfd7fe687f2b0d35f365e76468a7e0e2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="implement-an-abstract-class-in-c"></a>Implémenter une classe abstraite en c# #
**Ce que :** vous permet de générer d’immédiatement le code requis pour implémenter une classe abstraite. 

**Quand :** vous voulez hériter d’une classe abstraite.  

**Pourquoi :** vous pouvez implémenter manuellement de tous les membres abstraits un par un, mais cette fonctionnalité génère automatiquement toutes les signatures de méthode. 

**Comment faire :**

1. Placez votre curseur sur la ligne où il existe une ligne ondulée rouge, indiquant vous avez hérité d’une classe abstraite, mais n’avez pas implémenté toutes les membres requis.

   ![Code en surbrillance](media/abstract_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **implémenter une classe abstraite** à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Avec le bouton droit et sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **implémenter une classe abstraite** à partir du message de fenêtre d’aperçu.
     * Placez le curseur sur la ligne ondulée rouge et cliquez sur le ![Ampoule](media/bulb.png) icône qui s’affiche.
     * Cliquez sur le bouton ![Ampoule](media/bulb.png) icône qui apparaît dans la marge de gauche, si le curseur de texte se trouve déjà sur la ligne de la ligne ondulée rouge.

   ![Aperçu de classe d’implémentation](media/abstract_preview.png)

   >[!TIP]
   >Utilisez le [ **aperçu des modifications** ](../../ide/preview-changes.md) lien en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.
   >
   >En outre, vous pouvez utiliser la **Document**, **projet**, et **Solution** liens en bas de la fenêtre d’aperçu pour créer les signatures de méthode approprié sur plusieurs classes qui héritent de la classe abstraite.

1. Les signatures de méthode abstraite seront créés automatiquement, prêt à être implémentée.

   ![Implémenter le résultat de la classe](media/abstract_result.png)

## <a name="see-also"></a>Voir aussi  
[Génération de code (C#)](../code-generation-csharp.md)  
[Aperçu des modifications](../../ide/preview-changes.md)
