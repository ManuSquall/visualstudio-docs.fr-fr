---
title: "Générer des substitutions des méthodes Equals et GetHashCode - génération de code (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 56b1753dbdcfbf8ce318e964a16879f02b1482c4
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2018
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-c"></a>Générer des substitutions des méthodes Equals et GetHashCode en C# #

**Quoi :** vous permet de générer les méthodes **Equals** et **GetHashCode**.

**Quand :** générez ces substitutions lorsque vous disposez d’un type qui représente une « valeur » qui doit être comparée selon certains champs plutôt que par l’emplacement de l’objet en mémoire.

**Pourquoi :** si vous implémentez un type de valeur, vous pouvez substituer la méthode Equals afin d’améliorer les performances par rapport à l’implémentation par défaut de la méthode Equals sur ValueType.

Si vous implémentez un type de référence, vous pouvez substituer la méthode Equals si votre type ressemble à un type de base, par exemple Point, String, BigNumber, etc.

Substituez la méthode GetHashCode pour permettre à un type de fonctionner correctement dans une table de hachage. Consultez la section sur les [opérateurs d’égalité](/dotnet/standard/design-guidelines/equality-operators).

**Comment :**

1. Placez votre curseur dans votre déclaration de type.

   ![Code mis en surbrillance](media/overrides-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Générer Equals(object)** ou **Générer Equals et GetHashCode** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Générer Equals(object)** ou **Générer Equals et GetHashCode** dans la fenêtre contextuelle d’aperçu.
     * Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne avec la déclaration de type.

   ![Générer un aperçu des substitutions](media/overrides-preview-cs.png)

1. Sélectionnez les membres pour lesquels vous souhaitez générer les méthodes de substitution :

    ![Boîte de dialogue Générer les substitutions](media/overrides-dialog-cs.png)

    > [!TIP]
    > Vous pouvez également choisir de générer des opérateurs à partir de cette boîte de dialogue en utilisant les cases à cocher situées sous la liste des membres.

1. Les substitutions Equals et GetHashCode seront générées avec les implémentations par défaut automatiques.

   ![Résultat de l’action Générer une méthode](media/overrides-result-cs.png)

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)
