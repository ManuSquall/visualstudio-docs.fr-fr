---
title: "Générer un constructeur - génération de Code (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2280cfa-a9ec-4b56-9d94-c8fd384db980
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 53b1ab5cb202995cb6a5e9eeef76ee4cf38b4ea9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="generate-a-constructor-in-visual-basic"></a>Générer un constructeur en Visual Basic
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
[Génération de code (Visual Basic)](../code-generation-vb.md)  
[Aperçu des modifications](../../ide/preview-changes.md)