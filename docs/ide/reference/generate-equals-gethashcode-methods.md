---
title: "Générer des substitutions des méthodes C# Equals et GetHashCode dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: dc380985231937073bff1cb9ce275c38eb70448f
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Générer des substitutions des méthodes Equals et GetHashCode dans Visual Studio

Cette génération de code s’applique à :

- C#

**Quoi :** vous permet de générer les méthodes **Equals** et **GetHashCode**.

**Quand :** générez ces substitutions quand vous disposez d’un type qui doit être comparé selon un ou plusieurs champs et non selon l’emplacement de l’objet en mémoire.

**Pourquoi :**

- si vous implémentez un type de valeur, vous pouvez substituer la méthode **Equals** afin d’améliorer les performances par rapport à l’implémentation par défaut de la méthode Equals sur ValueType.

- Si vous implémentez un type de référence, vous pouvez substituer la méthode **Equals** si votre type ressemble à un type de base, par exemple Point, String, BigNumber, etc.

- Substituez la méthode **GetHashCode** pour permettre à un type de fonctionner correctement dans une table de hachage. Consultez la section sur les [opérateurs d’égalité](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Procédure

1. Placez votre curseur dans votre déclaration de type.

   ![Code mis en surbrillance](media/overrides-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
     - Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
     - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
     - Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne avec la déclaration de type.

   ![Générer un aperçu des substitutions](media/overrides-preview-cs.png)

1. Sélectionnez **Générer Equals(object)** ou **Générer Equals et GetHashCode** dans le menu déroulant.

1. Dans la boîte de dialogue **Choisir les membres**, sélectionnez les membres pour lesquels vous souhaitez générer des méthodes :

    ![Boîte de dialogue Générer les substitutions](media/overrides-dialog-cs.png)

    > [!TIP]
    > Vous pouvez également choisir de générer des opérateurs à partir de cette boîte de dialogue en utilisant les cases à cocher situées sous la liste des membres.

   Les substitutions Equals et GetHashCode sont générées avec des implémentations par défaut.

   ![Résultat de l’action Générer une méthode](media/overrides-result-cs.png)

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)
