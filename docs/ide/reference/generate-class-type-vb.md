---
title: "Générer une classe ou un type - génération de code (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vsl.GenerateFromUsage
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: 4a4ff45a59fb53964a365f31cc4d5f48a5b159dc
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-class-or-type-in-visual-basic"></a>Générer une classe ou un type dans Visual Basic
**Quoi :** vous permet de générer immédiatement le code pour une classe ou un type. 

**Quand :** vous introduisez une nouvelle classe ou un nouveau type et souhaitez les déclarer correctement, automatiquement.  

**Pourquoi :** vous pouvez déclarer la classe ou le type avant de l’utiliser, mais cette fonctionnalité générera automatiquement la classe ou le type. 

**Comment :**

1. Placez votre curseur sur la ligne ondulée rouge indiquant que vous avez utilisé une classe qui n’existe pas encore.

   ![Code mis en surbrillance](media/class-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez l’une des options dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez l’une des options dans la fenêtre contextuelle d’aperçu.
     * Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![Ampoule](media/bulb-vb.png) qui apparaît.
     * Cliquez sur le bouton ![Ampoule](media/bulb-vb.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

   ![Aperçu de l’action Générer la classe](media/class-preview-vb.png)

   Sélection | Description
   --- | ---
   Générer la classe '*TypeName*' dans un nouveau fichier | Crée une classe nommée *TypeName* dans un fichier nommé *TypeName*.cs/.vb
   Générer la classe '*TypeName*' | Crée une classe nommée *TypeName* dans le fichier actuel.
   Générer la classe imbriquée ’*TypeName*' | Crée une classe nommée *TypeName* imbriquée dans la classe actuelle.
   Générer un nouveau type... | Crée une nouvelle classe ou structure avec toutes les propriétés que vous spécifiez.

   >[!TIP]
   >Utilisez le lien [**Aperçu des modifications**](../../ide/preview-changes.md) en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.

1. Si vous sélectionnez l’élément **Générer un nouveau type...** , une boîte de dialogue s’affiche et vous permet d’effectuer des actions supplémentaires.

   ![Générer le type](media/class-newtype-vb.png)

   Sélection | Description
   --- | ---
   Accès | Définissez un accès *Par défaut*, *Interne* ou *Public* pour le type.
   Genre | Peut être défini sur *classe* ou *structure*.
   Name | Ce paramètre ne peut pas être modifié et affichera le nom que vous avez déjà tapé.
   Projet | Si votre solution contient plusieurs projets, vous pouvez choisir l’emplacement souhaité pour la classe/structure à utiliser.
   Nom du fichier | Vous pouvez créer un nouveau fichier, ou ajouter le type à un fichier existant.

1. La classe/structure sera créée automatiquement avec le constructeur déduit de son utilisation.

   ![Résultat de l’action Générer la classe](media/class-result-vb.png)

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)