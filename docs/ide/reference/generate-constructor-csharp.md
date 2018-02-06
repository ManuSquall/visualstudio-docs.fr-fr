---
title: "Générer un constructeur - génération de code (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: b6e73b3b012547e98934bbcd76d1ee2eb0f3324d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="generate-a-constructor-in-c"></a>Générer un constructeur en C# #
**Quoi :** vous permet de générer immédiatement le code pour un nouveau constructeur sur une classe. 

**Quand :** vous introduisez un nouveau constructeur et souhaitez le déclarer correctement, automatiquement, ou que vous modifiez un constructeur existant. 

**Pourquoi :** vous pouvez déclarer le constructeur avant de l’utiliser, mais cette fonctionnalité le générera automatiquement avec les paramètres appropriés. En outre, la modification d’un constructeur existant nécessite la mise à jour de tous les sites d’appel, sauf si vous utilisez cette fonctionnalité pour les mettre automatiquement à jour.

**Comment :** il existe plusieurs façons de générer un constructeur :
- [Générer un constructeur et choisir des membres](#pick)
- [Générer un constructeur à partir des champs sélectionnés](#selection)
- [Générer un constructeur à partir d’une nouvelle utilisation](#usage)
- [Ajouter un paramètre au constructeur existant](#addparameter)
- [Créer et initialiser le champ/la propriété à partir d’un paramètre de constructeur](#create)

## <a id = "pick"></a>Générer un constructeur et choisir des membres
1. Placez votre curseur dans une ligne vide d’une classe :

   ![Curseur dans une ligne vide](media/constructor1-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Générer le constructeur...** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Générer le constructeur...** dans la fenêtre contextuelle d’aperçu.
     * Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne vide dans la classe.

   ![Générer l’aperçu du constructeur](media/constructor1-preview-cs.png)

1. Une boîte de dialogue apparaît et vous permet de choisir les membres à utiliser comme paramètres du constructeur ainsi que leur ordre (à l’aide des flèches haut et bas). Appuyez sur **Ok** pour valider vos modifications.
  
   ![Boîte de dialogue Choisir les membres](media/constructor1-dialog-cs.png)

   >[!TIP] 
   >Vous pouvez cocher la case **Ajouter des contrôles de valeur null** pour générer automatiquement des contrôles de valeur null pour les paramètres de votre constructeur.

1. Le constructeur sera créé avec les paramètres sélectionnés dans l’ordre spécifié.
   ![Résultat de l’action Générer le constructeur](media/constructor1-result-cs.png)

## <a id="selection"></a>Générer le constructeur à partir des champs sélectionnés
1. Mettez en surbrillance les membres que vous souhaitez inclure dans votre constructeur généré : ![Mettre en surbrillance les membres](media/constructor2-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Générer le constructeur 'TypeName(...)'** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Générer le constructeur 'TypeName(...)'** dans la fenêtre contextuelle d’aperçu.
     * Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne avec la sélection.

     ![Aperçu Générer le constructeur](media/constructor2-preview-cs.png)

1. Le constructeur sera créé avec les paramètres sélectionnés.
     ![Résultat de l’action Générer le constructeur](media/constructor2-result-cs.png)

## <a id="usage"></a>Générer un constructeur à partir d’une nouvelle utilisation
1. Placez votre curseur sur la ligne ondulée rouge indiquant que vous avez utilisé un constructeur qui n’existe pas encore.

   ![Code mis en surbrillance](media/constructor-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Générer le constructeur dans '*TypeName*'** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Générer le constructeur dans '*TypeName*'** dans la fenêtre contextuelle d’aperçu.
     * Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![Ampoule](media/bulb-cs.png) qui apparaît.
     * Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

   ![Générer l’aperçu du constructeur](media/constructor-preview-cs.png)

   >[!TIP]
   >Utilisez le lien [**Aperçu des modifications**](../../ide/preview-changes.md) en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.

1. Le constructeur sera créé automatiquement avec les paramètres déduits de son utilisation.

   ![Résultat de l’action Générer le constructeur](media/constructor-result-cs.png)

## <a id="addparameter"></a>Ajouter un paramètre au constructeur existant
1. Ajoutez un paramètre à une instanciation d’objet existante.

1. Placez votre curseur sur la ligne ondulée rouge indiquant que vous avez utilisé un constructeur qui n’existe pas encore.
    
    ![Mise en surbrillance de l’option Générer le constructeur](media/constructor4-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Ajouter un paramètre à 'TypeName(...)'** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Ajouter un paramètre à 'TypeName(...)'** dans la fenêtre contextuelle d’aperçu.
     * Placez le curseur sur la ligne ondulée rouge, puis cliquez sur l’icône ![Ampoule](media/bulb-cs.png) qui apparaît.
     * Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne ondulée rouge.

    ![Générer l’aperçu du constructeur](media/constructor4-preview-cs.png)

1. Le paramètre sera automatiquement ajouté à son type en fonction de son utilisation.
   
   ![Résultat de l’action Générer le constructeur](media/constructor4-result-cs.png)

## <a id="create"></a>Créer et initialiser le champ/la propriété à partir d’un paramètre de constructeur
1. À partir d’un constructeur existant, ajoutez un paramètre :

   ![Mise en surbrillance de l’option Générer le constructeur](media/constructor5-highlight-cs.png)

1. Placez votre curseur dans le paramètre qui vient d’être ajouté.

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Créer et initialiser la propriété 'YourProperty'** ou **Créer et initialiser le champ 'YourField'** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Cliquez avec le bouton droit et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Créer et initialiser la propriété 'YourProperty'** ou **Créer et initialiser le champ 'YourField'** dans la fenêtre contextuelle d’aperçu.
     * Cliquez sur le bouton ![Ampoule](media/bulb-cs.png) qui apparaît dans la marge de gauche si le curseur de texte se trouve déjà sur la ligne avec le paramètre ajouté.

   ![Générer l’aperçu du constructeur](media/constructor5-preview-cs.png)

1. Le champ ou la propriété seront créés et nommés automatiquement pour correspondre à vos types.

   ![Résultat de l’action Générer le constructeur](media/constructor5-result-cs.png)

## <a name="see-also"></a>Voir aussi

[Génération de code](../code-generation-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)