---
title: "Générer une classe ou un type de génération de Code (c#) - | Documents Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vsl.GenerateFromUsage
dev_langs: csharp
ms.openlocfilehash: b6825be5447718e47f7145b0b3b16ec6d0ee076c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-class-or-type-in-c"></a>Générer une classe ou un type en langage c# #
**Ce que :** vous permet de générer d’immédiatement le code pour une classe ou un type. 

**Quand :** vous introduire une nouvelle classe ou un type et que vous souhaitez correctement la déclarer, automatiquement.  

**Pourquoi :** vous pouviez déclarer la classe ou type avant de l’utiliser, mais cette fonctionnalité sera générer la classe ou de type automatiquement. 

**Comment faire :**

1. Placez votre curseur sur la ligne où il existe une ligne ondulée rouge, indiquant que vous avez utilisé une classe qui n’existe pas encore.

   ![Code en surbrillance](media/class_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez une des options dans le message de fenêtre d’aperçu.
   * **Souris**
     * Avec le bouton droit et sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez une des options dans le message de fenêtre d’aperçu.
     * Placez le curseur sur la ligne ondulée rouge et cliquez sur le ![Ampoule](media/bulb.png) icône qui s’affiche.
     * Cliquez sur le bouton ![Ampoule](media/bulb.png) icône qui apparaît dans la marge de gauche, si le curseur de texte se trouve déjà sur la ligne de la ligne ondulée rouge.

   ![Génération d’un aperçu de classe](media/class_preview.png)

   Sélection | Description
   --- | ---
   Générer la classe*TypeName*' dans le nouveau fichier | Crée une classe nommée *TypeName* dans un fichier nommé *TypeName*.cs/.vb
   Générer la classe*TypeName*' | Crée une classe nommée *TypeName* dans le fichier actuel.
   Générer des classes imbriquées*TypeName*' | Crée une classe nommée *TypeName* imbriquée dans la classe actuelle.
   Générer un nouveau type... | Crée une nouvelle classe ou un struct avec toutes les propriétés que vous spécifiez.

   >[!TIP]
   >Utilisez le [ **aperçu des modifications** ](../../ide/preview-changes.md) lien en bas de la fenêtre d’aperçu pour voir toutes les modifications qui seront apportées avant d’effectuer votre sélection.

1. Si vous sélectionnez le **générer un nouveau type...**  élément, une boîte de dialogue s’affiche qui vous permet d’effectuer des actions supplémentaires.

   ![Générer le type](media/class_newtype.png)

   Sélection | Description
   --- | ---
   Accès | Définir le type d’avoir *par défaut*, *interne* ou *Public* accès.
   Genre | Cela peut être défini en tant que *classe* ou *struct*.
   Nom | Cela ne peut pas être modifiée et sera le nom que vous avez déjà tapé.
   Projet | S’il existe plusieurs projets dans votre solution, vous pouvez choisir l’emplacement souhaité pour la classe/struct de vie.
   Nom du fichier | Vous pouvez créer un nouveau fichier, ou vous pouvez ajouter le type à un fichier existant.

1. La classe/struct est créée automatiquement avec le constructeur à partir de son utilisation.

   ![Générer des résultats de la classe](media/class_result.png)

## <a name="see-also"></a>Voir aussi  
[Génération de code (C#)](../code-generation-csharp.md)  
[Aperçu des modifications](../../ide/preview-changes.md)