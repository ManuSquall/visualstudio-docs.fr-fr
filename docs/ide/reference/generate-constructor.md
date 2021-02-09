---
title: Action rapide Générer un constructeur
description: Découvrez comment utiliser le menu actions rapides et refactorisations pour générer immédiatement le code d’un nouveau constructeur sur une classe.
ms.custom: SEO-VS-2020
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 24e9324444dbeb10a86184f7c15ea8b88e118177
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898053"
---
# <a name="generate-a-constructor-in-visual-studio"></a>Générer un constructeur dans Visual Basic

Cette génération de code s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de générer immédiatement le code pour un nouveau constructeur sur une classe.

**Quand :** vous introduisez un nouveau constructeur et souhaitez le déclarer correctement, automatiquement, ou que vous modifiez un constructeur existant.

**Pourquoi :** vous pouvez déclarer le constructeur avant de l’utiliser, mais cette fonctionnalité le générera automatiquement avec les paramètres appropriés. En outre, la modification d’un constructeur existant nécessite la mise à jour de tous les sites d’appel, sauf si vous utilisez cette fonctionnalité pour les mettre automatiquement à jour.

**Comment :** il existe plusieurs façons de générer un constructeur :

- [Générer un constructeur et choisir des membres](#pick)
- [Générer un constructeur avec des propriétés](#with)
- [Générer le constructeur à partir des champs sélectionnés](#selection)
- [Générer un constructeur à partir d’une nouvelle utilisation](#usage)
- [Ajouter un paramètre au constructeur existant](#addparameter)
- [Créer et initialiser le champ/la propriété à partir d’un paramètre de constructeur](#create)

## <a name="generate-constructor-and-pick-members-c-only"></a><a id = "pick"></a> Générer un constructeur et choisir des membres (C# uniquement)

1. Placez votre curseur dans une ligne vide d’une classe :

   ![Curseur dans une ligne vide](media/constructor1-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Cliquez sur l' :::image type="icon" source="media/screwdriver.png"::: icône qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne vide dans la classe.

   ![Capture d’écran de l’option de création de constructeur.](media/constructor1-preview-cs.png)

1. Sélectionnez **Générer le constructeur** dans le menu déroulant.

   La boîte de dialogue **Choisir les membres** s’ouvre.

1. Choisissez les membres à inclure comme paramètres du constructeur. Vous pouvez les organiser à l’aide des flèches haut et bas. Choisissez **OK**.

   ![Boîte de dialogue Choisir les membres](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Vous pouvez cocher la case **Ajouter des contrôles de valeur null** pour générer automatiquement des contrôles de valeur null pour les paramètres de votre constructeur.

   Le constructeur est créé avec les paramètres sélectionnés.

   ![Capture d’écran montrant que le constructeur est créé avec les paramètres spécifiés.](media/constructor1-result-cs.png)

## <a name="generate-constructor-with-properties-c-only"></a><a id = "with"></a> Générer un constructeur avec des propriétés (C# uniquement)

1. Placez le curseur sur l’instance.

2. Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.

3. Sélectionnez **générer le constructeur dans `<QualifiedName>` (avec les propriétés)**.

   ![Capture d’écran de l’option générer le constructeur dans la clé (avec les propriétés).](media/generate-constructor-with-properties.png)

## <a name="generate-constructor-from-selected-fields-c-only"></a><a id="selection"></a> Générer le constructeur à partir des champs sélectionnés (C# uniquement)

1. Mettez en surbrillance les membres à inclure dans votre constructeur généré :

   ![Mettre en surbrillance les membres](media/constructor2-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Cliquez sur l' :::image type="icon" source="media/screwdriver.png"::: icône qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne avec la sélection.

      ![Capture d’écran de l’option de chaîne de chaîne de la personne générer le constructeur.](media/constructor2-preview-cs.png)

1. Sélectionnez **Générer le constructeur 'TypeName(...)'** dans le menu déroulant.

   Le constructeur est créé avec les paramètres sélectionnés.

   ![Capture d’écran montrant que le constructeur est créé avec les paramètres sélectionnés.](media/constructor2-result-cs.png)

## <a name="generate-constructor-from-new-usage-c-and-visual-basic"></a><a id="usage"></a> Générer un constructeur à partir d’une nouvelle utilisation (C# et Visual Basic)

1. Placez votre curseur sur la ligne présentant un trait rouge ondulé. Celle-ci indique un appel à un constructeur qui n’existe pas encore.

   - C# :

       ![Code C# mis en surbrillance](media/constructor-highlight-cs.png)

   - Visual Basic :

       ![Code VB mis en surbrillance](media/constructor-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Pointez sur le tilde rouge, puis cliquez sur l' :::image type="icon" source="media/error-bulb.png"::: icône qui s’affiche.
      - Cliquez sur l' :::image type="icon" source="media/error-bulb.png"::: icône qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne avec le tilde rouge.

      ![Capture d’écran de l’option générer le constructeur en personne.](media/constructor-preview-cs.png)

3. Sélectionnez **Générer le constructeur dans '*TypeName*'** dans le menu déroulant.

   > [!TIP]
   > Utilisez le lien **Aperçu des modifications** en bas de la fenêtre d’aperçu [pour voir tous les changements](../../ide/preview-changes.md) qui seront apportés avant d’effectuer votre sélection.

   Le constructeur est créé avec les paramètres déduits de son utilisation.

   - C# :

       ![Résultat de l’action Générer une méthode (C#)](media/constructor-result-cs.png)

   - Visual Basic :

       ![Résultat de l’action Générer une méthode (VB)](media/constructor-result-vb.png)

## <a name="add-parameter-to-existing-constructor-c-only"></a><a id="addparameter"></a> Ajouter un paramètre au constructeur existant (C# uniquement)

1. Ajoutez un paramètre à un appel de constructeur existant.

2. Placez votre curseur sur la ligne ondulée rouge indiquant que vous avez utilisé un constructeur qui n’existe pas encore.

    ![Capture d’écran montrant la ligne où se trouve un tilde rouge.](media/constructor4-highlight-cs.png)

3. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Pointez sur le tilde rouge, puis cliquez sur l' :::image type="icon" source="media/error-bulb.png"::: icône qui s’affiche.
      - Cliquez sur l' :::image type="icon" source="media/error-bulb.png"::: icône qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne avec le tilde rouge.

      ![Capture d’écran de l’option Ajouter un paramètre à la chaîne Person.](media/constructor4-preview-cs.png)

4. Sélectionnez **Ajouter un paramètre à 'TypeName(...)'** dans le menu déroulant.

   Le paramètre est ajouté au constructeur, son type étant déduit de son utilisation.

   ![Capture d’écran montrant que le paramètre est ajouté au constructeur, son type déduit de son utilisation.](media/constructor4-result-cs.png)

Vous pouvez également ajouter un paramètre à une méthode existante. Pour plus d’informations, voir [Ajouter un paramètre à une méthode](add-parameter.md).

## <a name="create-and-initialize-a-field-or-property-from-a-constructor-parameter-c-only"></a><a id="create"></a> Créer et initialiser un champ ou une propriété à partir d’un paramètre de constructeur (C# uniquement)

1. Trouvez un constructeur existant et ajoutez un paramètre :

   ![Capture d’écran montrant un constructeur existant.](media/constructor5-highlight-cs.png)

1. Placez votre curseur dans le paramètre qui vient d’être ajouté.

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
      - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
      - Cliquez sur l' :::image type="icon" source="media/screwdriver.png"::: icône qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne avec le paramètre ajouté.

   ![Capture d’écran de l’option de création et d’initialisation de l’âge des propriétés.](media/constructor5-preview-cs.png)

1. Sélectionnez **Créer et initialiser la propriété** ou **Créer et initialiser le champ** dans le menu déroulant.

   Le champ ou la propriété est déclarée et automatiquement nommée pour correspondre à vos types. Une ligne de code est également ajoutée pour initialiser le champ ou la propriété dans le corps du constructeur.

   ![Capture d’écran montrant que le champ ou la propriété est déclaré et nommé automatiquement pour correspondre à vos types.](media/constructor5-result-cs.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Prévisualiser les modifications](../../ide/preview-changes.md)
