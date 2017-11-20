---
title: "Générer un constructeur - génération de Code (c#) | Documents Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31b0a187e0640a94d9401a1e20fd03d81ff5b920
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-constructor-in-c"></a>Générer un constructeur en c# #
**Ce que :** vous permet de générer d’immédiatement le code pour un nouveau constructeur sur une classe. 

**Quand :** vous introduire un nouveau constructeur et que vous souhaitez correctement la déclarer, automatiquement.  

**Pourquoi :** vous pouviez déclarer le constructeur avant de l’utiliser, mais cette fonctionnalité génère, avec les paramètres appropriés, automatiquement. 

**Comment faire :**

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
  
## <a name="see-also"></a>Voir aussi  
[Génération de code (C#)](../code-generation-csharp.md)  
[Aperçu des modifications](../../ide/preview-changes.md)