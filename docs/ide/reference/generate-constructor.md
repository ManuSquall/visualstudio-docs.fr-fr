---
title: Générer un constructeur dans Visual Basic
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 091caf9db4152b7c349fdf717d97639b360bb602
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513022"
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
   - [Générer un constructeur à partir des champs sélectionnés](#selection)
   - [Générer un constructeur à partir d’une nouvelle utilisation](#usage)
   - [Ajouter un paramètre au constructeur existant](#addparameter)
   - [Créer et initialiser le champ/la propriété à partir d’un paramètre de constructeur](#create)

## <a id = "pick"></a> Générer un constructeur et choisir des membres (C# uniquement)

1. Placez votre curseur dans une ligne vide d’une classe :

   ![Curseur dans une ligne vide](media/constructor1-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
     - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
     - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
     - Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne vide dans la classe.

   ![Générer l’aperçu du constructeur](media/constructor1-preview-cs.png)

1. Sélectionnez **Générer le constructeur** dans le menu déroulant.

   La boîte de dialogue **Choisir les membres** s’ouvre.

1. Choisissez les membres à inclure comme paramètres du constructeur. Vous pouvez les organiser à l’aide des flèches haut et bas. Cliquez sur **OK**.

   ![Boîte de dialogue Choisir les membres](media/constructor1-dialog-cs.png)

   > [!TIP]
   > Vous pouvez cocher la case **Ajouter des contrôles de valeur null** pour générer automatiquement des contrôles de valeur null pour les paramètres de votre constructeur.

   Le constructeur est créé avec les paramètres sélectionnés.

   ![Résultat de l’action Générer le constructeur](media/constructor1-result-cs.png)

## <a id="selection"></a> Générer le constructeur à partir des champs sélectionnés (C# uniquement)

1. Mettez en surbrillance les membres à inclure dans votre constructeur généré :

   ![Mettre en surbrillance les membres](media/constructor2-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
     - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
     - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
     - Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne avec la sélection.

     ![Aperçu Générer le constructeur](media/constructor2-preview-cs.png)

1. Sélectionnez **Générer le constructeur 'TypeName(...)'** dans le menu déroulant.

   Le constructeur est créé avec les paramètres sélectionnés.

   ![Résultat de l’action Générer le constructeur](media/constructor2-result-cs.png)

## <a id="usage"></a> Générer un constructeur à partir d’une nouvelle utilisation (C# et Visual Basic)

1. Placez votre curseur sur la ligne présentant un trait rouge ondulé. Celle-ci indique un appel à un constructeur qui n’existe pas encore.

   - C# :

    ![Code C# mis en surbrillance](media/constructor-highlight-cs.png)

   - Visual Basic :

    ![Code VB mis en surbrillance](media/constructor-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
     - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
     - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
     - Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![Ampoule](media/bulb-cs.png) qui apparaît.
     - Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

    ![Générer l’aperçu du constructeur](media/constructor-preview-cs.png)

1. Sélectionnez **Générer le constructeur dans '*TypeName*'** dans le menu déroulant.

   > [!TIP]
   > Utilisez le lien **Aperçu des modifications** en bas de la fenêtre d’aperçu [pour voir tous les changements](../../ide/preview-changes.md) qui seront apportés avant d’effectuer votre sélection.

   Le constructeur est créé avec les paramètres déduits de son utilisation.

   - C# :

      ![Résultat de l’action Générer une méthode (C#)](media/constructor-result-cs.png)

   - Visual Basic :

      ![Résultat de l’action Générer une méthode (VB)](media/constructor-result-vb.png)

## <a id="addparameter"></a> Ajouter un paramètre au constructeur existant (C# uniquement)

1. Ajoutez un paramètre à un appel de constructeur existant.

1. Placez votre curseur sur la ligne ondulée rouge indiquant que vous avez utilisé un constructeur qui n’existe pas encore.

    ![Mise en surbrillance de l’option Générer le constructeur](media/constructor4-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
     - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
     - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
     - Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![Ampoule](media/bulb-cs.png) qui apparaît.
     - Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

    ![Générer l’aperçu du constructeur](media/constructor4-preview-cs.png)

1. Sélectionnez **Ajouter un paramètre à 'TypeName(...)'** dans le menu déroulant.

   Le paramètre est ajouté au constructeur, son type étant déduit de son utilisation.

   ![Résultat de l’action Générer le constructeur](media/constructor4-result-cs.png)

## <a id="create"></a> Créer et initialiser un champ ou une propriété à partir d’un paramètre de constructeur (C# uniquement)

1. Trouvez un constructeur existant et ajoutez un paramètre :

   ![Mise en surbrillance de l’option Générer le constructeur](media/constructor5-highlight-cs.png)

1. Placez votre curseur dans le paramètre qui vient d’être ajouté.

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
     - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**.
   - **Souris**
     - Cliquez avec le bouton droit et sélectionnez le menu **Actions rapides et refactorisations**.
     - Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne avec le paramètre ajouté.

   ![Générer l’aperçu du constructeur](media/constructor5-preview-cs.png)

1. Sélectionnez **Créer et initialiser la propriété** ou **Créer et initialiser le champ**  dans le menu déroulant.

   Le champ ou la propriété est déclarée et automatiquement nommée pour correspondre à vos types. Une ligne de code est également ajoutée pour initialiser le champ ou la propriété dans le corps du constructeur.

   ![Résultat de l’action Générer le constructeur](media/constructor5-result-cs.png)

## <a name="see-also"></a>Voir aussi

- [Génération de code](../code-generation-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)