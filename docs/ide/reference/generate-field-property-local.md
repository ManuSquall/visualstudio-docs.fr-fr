---
title: "Générer un champ, une propriété ou une variable locale dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 4e5da77f3053aabc2e8e4813c8ef5e7fb3407b5f
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Générer un champ, une propriété ou une variable locale dans Visual Studio

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de générer immédiatement le code d’un champ, d’une propriété ou d’une valeur locale non déclarée précédemment.

**Quand :** vous introduisez un nouveau champ, une nouvelle propriété ou une nouvelle valeur locale lors de la saisie et que vous souhaitez correctement déclarer cet élément, automatiquement.

**Pourquoi :** vous pouvez déclarer le champ, la propriété ou la valeur locale avant de l’utiliser, mais cette fonctionnalité générera automatiquement la déclaration et le type.

## <a name="how-to"></a>Procédure

1. Placez votre curseur sur la ligne présentant un trait rouge ondulé. Celui-ci indique un champ, une variable locale ou une propriété qui n’existe pas encore.

   - C# :

    ![Code C# mis en surbrillance](media/field-highlight-cs.png)

   - Visual Basic :

    ![Code VB mis en surbrillance](media/field-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
     - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
     - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
     - Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![Ampoule](media/bulb-cs.png) qui apparaît.
     - Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

    ![Aperçu de l’action Générer le champ/la propriété/la valeur locale](media/field-preview-cs.png)

1. Sélectionnez l’une des options de génération dans le menu déroulant.

   > [!TIP]
   > Utilisez le lien **Aperçu des modifications** en bas de la fenêtre d’aperçu [pour voir tous les changements](../../ide/preview-changes.md) qui seront apportés avant d’effectuer votre sélection.

   Le champ, la propriété ou la variable locale est créé avec le type déduit de son utilisation.

   - C# :

      ![Résultat de l’action Générer une méthode (C#)](media/field-result-cs.png)

   - Visual Basic :

      ![Résultat de l’action Générer une méthode (VB)](media/field-result-vb.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)
