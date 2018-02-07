---
title: "Générer un champ, une propriété ou une valeur locale - génération de code (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 766311f0ba165c87e61bb873baa3ab2f0b2d1402
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2018
---
# <a name="generate-a-field-property-or-local-in-visual-basic"></a>Générer un champ, une propriété ou une valeur locale dans Visual Basic
**Quoi :** vous permet de générer immédiatement le code d’un champ, d’une propriété ou d’une valeur locale non déclarée précédemment. 

**Quand :** vous introduisez un nouveau champ, une nouvelle propriété ou une nouvelle valeur locale lors de la saisie et que vous souhaitez correctement déclarer cet élément, automatiquement.  

**Pourquoi :** vous pouvez déclarer le champ, la propriété ou la valeur locale avant de l’utiliser, mais cette fonctionnalité générera automatiquement la déclaration et le type. 

**Comment :**

1. Placez votre curseur sur la ligne ondulée rouge indiquant que vous avez utilisé un champ, une propriété ou une valeur locale qui n’existe pas encore.

   ![Code mis en surbrillance](media/field-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Générer la variable '*Name*' > Générer le champ/la propriété/la valeur locale** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Générer la variable '*Name*' > Générer le champ/la propriété/la valeur locale** dans la fenêtre contextuelle d’aperçu.
     * Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![Ampoule](media/bulb-vb.png) qui apparaît.
     * Cliquez sur le bouton ![Ampoule](media/bulb-vb.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

   ![Aperçu de l’action Générer le champ/la propriété/la valeur locale](media/field-preview-vb.png)

   >[!TIP]
   >Utilisez le lien [**Aperçu des modifications**](../../ide/preview-changes.md) en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.

1. Le champ, la propriété ou la variable locale seront créés automatiquement avec le type déduit de leur utilisation.

   ![Résultat de l’action Générer le champ/la propriété/la valeur locale](media/field-result-vb.png)

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)