---
title: "Générer une méthode - génération de code (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 683790b4-b68b-42d7-8dc4-a68eca05aa01
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: e4caf80bec38305613111f290b80eafb74547598
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-method-in-c"></a>Générer une méthode en C# #
**Quoi :** vous permet d’ajouter immédiatement une méthode à une classe. 

**Quand :** vous introduisez une nouvelle méthode et souhaitez la déclarer correctement, automatiquement.  

**Pourquoi :** vous pouvez déclarer la méthode et ses paramètres avant de l’utiliser, mais cette fonctionnalité le générera automatiquement la déclaration. 

**Comment :**

1. Placez votre curseur sur la ligne ondulée rouge indiquant que vous avez utilisé une méthode qui n’existe pas encore.

   ![Code mis en surbrillance](media/method-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Générer la méthode** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Générer la méthode** dans la fenêtre contextuelle d’aperçu.
     * Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![Ampoule](media/bulb-cs.png) qui apparaît.
     * Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

   ![Générer un aperçu de méthode](media/method-preview-cs.png)

   >[!TIP]
   >Utilisez le lien [**Aperçu des modifications**](../../ide/preview-changes.md) en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.

1. La méthode sera créée automatiquement avec les paramètres déduits de son utilisation.

   ![Résultat de l’action Générer une méthode](media/method-result-cs.png)

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)
