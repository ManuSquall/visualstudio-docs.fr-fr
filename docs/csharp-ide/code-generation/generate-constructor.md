---
title: "Générer un constructeur - génération de Code (c#) | Documents Microsoft"
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
ms.openlocfilehash: 9ffa85d768939522935199edde6d0f19b3f2b7a2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-constructor-in-c"></a>Générer un constructeur en c# #
**Ce que :** vous permet de générer d’immédiatement le code pour un nouveau constructeur sur une classe. 

**Quand :** vous introduisez un nouveau constructeur et le souhaitez correctement déclarez-le automatiquement, ou modifier un constructeur existant. 

**Pourquoi :** vous pouviez déclarer le constructeur avant de l’utiliser, mais cette fonctionnalité génère, avec les paramètres appropriés, automatiquement. En outre, la modification d’un constructeur existant nécessite la mise à jour de tous les callsites les sauf si vous utilisez cette fonctionnalité pour mettre à jour automatiquement.

**Procédure :** il existe plusieurs façons pour générer un constructeur :
- [Générer de constructeur et sélectionner les membres](#pick)
- [Générer de constructeur à partir des champs sélectionnés](#selection)
- [Générer de constructeur à partir de la nouvelle utilisation](#usage)
- [Ajouter un paramètre au constructeur existant](#addparameter)
- [Créez et initialisez la propriété/champ à partir d’un paramètre de constructeur](#create)

## <a id = "pick"></a>Générer de constructeur et sélectionner les membres
1. Placez votre curseur dans n’importe quelle ligne vide dans une classe :

   ![Curseur dans la ligne vide](media/constructor1_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **générer constructeur...**  à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Avec le bouton droit et sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **générer constructeur...**  à partir du message de fenêtre d’aperçu.
     * Cliquez sur le bouton ![Ampoule](media/bulb.png) icône qui apparaît dans la marge de gauche, si le curseur de texte se trouve déjà sur la ligne vide dans la classe.

   ![Génération d’un aperçu du constructeur](media/constructor1_preview.png)

1. Une boîte de dialogue qui vous permet de sélectionner les membres à être utilisé en tant que paramètres du constructeur ainsi que leur ordre (avec le haut et vers le bas flèches). Appuyez sur **Ok** pour valider vos modifications.
  
   ![Boîte de dialogue de choix membres](media/constructor1_dialog.png)

   >[!TIP] 
   >Vous pouvez vérifier le **d’ajouter des vérifications null** case à cocher pour générer automatiquement les vérifications null pour les paramètres du constructeur.

1. Le constructeur sera créé avec les paramètres sélectionnés dans l’ordre spécifié.
   ![Générer le résultat de constructeur](media/constructor1_result.png)

## <a id="selection"></a>Générer de constructeur à partir des champs sélectionnés
1. Mettez en surbrillance les membres que vous souhaitez avoir dans votre constructeur généré : ![mettre en surbrillance les membres](media/constructor2_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **générer constructeur 'TypeName(...)'**  à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Avec le bouton droit et sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **générer constructeur 'TypeName(...)'**  à partir du message de fenêtre d’aperçu.
     * Cliquez sur le bouton ![Ampoule](media/bulb.png) icône qui apparaît dans la marge de gauche, si le curseur de texte est déjà sur la ligne de la sélection.

     ![Génération d’un aperçu du constructeur](media/constructor2_preview.png)

1. Le constructeur sera créé avec les paramètres sélectionnés.
     ![Générer le résultat de constructeur](media/constructor2_result.png)

## <a id="usage"></a>Générer de constructeur à partir de la nouvelle utilisation
1. Placez votre curseur sur la ligne où il existe une ligne ondulée rouge, indiquant vous avez utilisé un constructeur qui n’existe pas encore.

   ![Code en surbrillance](media/constructor_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez  **constructeur générer dans '*TypeName*' ** à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Avec le bouton droit et sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez  **constructeur générer dans '*TypeName*' ** à partir du message de fenêtre d’aperçu.
     * Placez le curseur sur la ligne ondulée rouge et cliquez sur le ![Ampoule](media/bulb.png) icône qui s’affiche.
     * Cliquez sur le bouton ![Ampoule](media/bulb.png) icône qui apparaît dans la marge de gauche, si le curseur de texte se trouve déjà sur la ligne de la ligne ondulée rouge.

   ![Génération d’un aperçu du constructeur](media/constructor_preview.png)

   >[!TIP]
   >Utilisez le [ **aperçu des modifications** ](../../ide/preview-changes.md) lien en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.

1. Le constructeur sera créé automatiquement avec les paramètres à partir de son utilisation.

   ![Générer le résultat de constructeur](media/constructor_result.png)

## <a id="selection"></a>Ajouter un paramètre au constructeur existant
1. Ajouter un paramètre à une instanciation d’objet existant.

1. Placez votre curseur sur la ligne où il existe une ligne ondulée rouge, indiquant vous avez utilisé un constructeur qui n’existe pas encore.
    
    ![Générer la mise en surbrillance du constructeur](media/constructor4_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **ajouter un paramètre de 'TypeName(...)'**  à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Avec le bouton droit et sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **ajouter un paramètre de 'TypeName(...)'**  à partir du message de fenêtre d’aperçu.
     * Placez le curseur sur la ligne ondulée rouge et cliquez sur le ![Ampoule](media/bulb.png) icône qui s’affiche.
     * Cliquez sur le bouton ![Ampoule](media/bulb.png) icône qui apparaît dans la marge de gauche, si le curseur de texte se trouve déjà sur la ligne de la ligne ondulée rouge.

    ![Génération d’un aperçu du constructeur](media/constructor4_preview.png)

1. Le paramètre sera ajouté automatiquement à son type déduit à partir de son utilisation.
   
   ![Générer le résultat de constructeur](media/constructor4_result.png)

## <a id="create"></a>Créez et initialisez la propriété/champ à partir d’un paramètre de constructeur
1. À partir d’un constructeur existant, ajoutez un paramètre :

   ![Générer la mise en surbrillance du constructeur](media/constructor5_highlight.png)

1. Placez votre curseur dans le paramètre qui vient d’être ajouté.

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **créer et initialiser la propriété 'YourProperty'** ou **création et initialisation de champ 'YourField'** à partir de la Message de fenêtre d’aperçu.
   * **Souris**
     * Avec le bouton droit et sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **créer et initialiser la propriété 'YourProperty'** ou **création et initialisation de champ 'YourField'**à partir du message de fenêtre d’aperçu.
     * Cliquez sur le bouton ![Ampoule](media/bulb.png) icône qui apparaît dans la marge de gauche, si le curseur de texte est déjà sur la ligne avec le paramètre ajouté.

   ![Génération d’un aperçu du constructeur](media/constructor5_preview.png)

1. La propriété/champ sera créée et nommée automatiquement pour correspondre à vos types.

   ![Générer le résultat de constructeur](media/constructor5_result.png)
  
## <a name="see-also"></a>Voir aussi  
[Génération de code (C#)](../code-generation-csharp.md)  
[Aperçu des modifications](../../ide/preview-changes.md)