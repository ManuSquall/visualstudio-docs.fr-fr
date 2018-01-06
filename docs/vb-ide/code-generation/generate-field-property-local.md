---
title: "Générer un champ, la propriété ou local - génération de Code (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c11888e0-31b1-44cc-9037-98d3f8b3623b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8e23dfa2b482a16d70ef71614ba35f9b20523aeb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-field-property-or-local-in-visual-basic"></a>Générer un champ, la propriété ou local en Visual Basic
**Ce que :** vous permet de générer d’immédiatement le code pour un champ non précédemment déclaré, propriété ou local. 

**Quand :** vous introduire un nouveau champ, la propriété ou local lors de la frappe et que vous souhaitez correctement la déclarer, automatiquement.  

**Pourquoi :** vous pouviez déclarer le champ, la propriété ou local avant de l’utiliser, mais cette fonctionnalité génère la déclaration et tapez automatiquement. 

**Comment faire :**

1. Placez votre curseur sur la ligne où il existe une ligne ondulée rouge indiquant vous avez utilisé un champ, local ou une propriété qui n’existe pas encore.

   ![Code en surbrillance](media/field_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez  **générer variable '*nom*' > champ/propriété Générer/local ** à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Avec le bouton droit et sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez  **générer variable '*nom*' > champ/propriété Générer/local ** depuis la version préliminaire menu contextuel de fenêtre.
     * Placez le curseur sur la ligne ondulée rouge et cliquez sur le ![Ampoule](media/bulb.png) icône qui s’affiche.
     * Cliquez sur le bouton ![Ampoule](media/bulb.png) icône qui apparaît dans la marge de gauche, si le curseur de texte se trouve déjà sur la ligne de la ligne ondulée rouge.

   ![Génération d’un aperçu du champ/propriété/local](media/field_preview.png)

   >[!TIP]
   >Utilisez le [ **aperçu des modifications** ](../../ide/preview-changes.md) lien en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.

1. Le champ, la propriété ou local est créé automatiquement avec le type déduit à partir de son utilisation.

   ![Générer des résultats de champ/propriété/local](media/field_result.png)

## <a name="see-also"></a>Voir aussi  
[Génération de code (Visual Basic)](../code-generation-vb.md)  
[Aperçu des modifications](../../ide/preview-changes.md)