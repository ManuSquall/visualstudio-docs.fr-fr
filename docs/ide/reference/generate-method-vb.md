---
title: "Générer une méthode - génération de code (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 08e46cb961ecd6511f79410a7424969f2db227ed
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-method-in-visual-basic"></a>Générer une méthode dans Visual Basic
**Quoi :** vous permet d’ajouter immédiatement une méthode à une classe. 

**Quand :** vous introduisez une nouvelle méthode et souhaitez la déclarer correctement, automatiquement.  

**Pourquoi :** vous pouvez déclarer la méthode et ses paramètres avant de l’utiliser, mais cette fonctionnalité le générera automatiquement la déclaration. 

**Comment :**

1. Placez votre curseur sur la ligne ondulée rouge indiquant que vous avez utilisé une méthode qui n’existe pas encore.

   ![Code mis en surbrillance](media/method-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Générer la méthode** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Générer la méthode** dans la fenêtre contextuelle d’aperçu.
     * Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![Ampoule](media/bulb-vb.png) qui apparaît.
     * Cliquez sur le bouton ![Ampoule](media/bulb-vb.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

   ![Générer un aperçu de méthode](media/method-preview-vb.png)

   >[!TIP]
   >Utilisez le lien [**Aperçu des modifications**](../../ide/preview-changes.md) en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.

1. La méthode sera créée automatiquement avec les paramètres déduits de son utilisation.

   ![Résultat de l’action Générer une méthode](media/method-result-vb.png)

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)