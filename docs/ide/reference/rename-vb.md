---
title: Refactoriser un changement de nom dans Visual Basic | Microsoft Docs
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0f9421ed314dc513d5e8af30bad907766342300a
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2018
---
# <a name="rename-a-code-symbol-in-visual-basic"></a>Renommer un symbole de code dans Visual Basic

**Quoi :** vous permet de renommer des identificateurs pour des symboles de code, tels que des champs, variables locales, méthodes, espaces de noms, propriétés et types.

**Quand :** vous voulez renommer en toute sécurité un élément sans avoir à rechercher toutes les instances et à copier/coller le nouveau nom.

**Pourquoi :** un copier-coller du nouveau nom dans un projet entier entraînera probablement des erreurs.  Cet outil de refactorisation effectuera avec précision le changement de nom.

**Comment :**

1. Mettez en surbrillance ou placez le curseur de texte dans l’élément à renommer :

   ![Code mis en surbrillance](media/rename-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+R**, puis **Ctrl+R**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
   * **Souris**
     * Sélectionnez **Modifier > Refactoriser > Renommer**.
     * Cliquez avec le bouton droit et sélectionnez **Renommer**.

1. Renommez l’élément en tapant le nouveau nom.

   ![Renommer une animation](media/rename-rename-vb.png)

   > [!TIP]
   > Vous pouvez également mettre à jour les commentaires et autres chaînes afin d’utiliser ce nouveau nom, et [afficher un aperçu des modifications](../../ide/preview-changes.md) avant de les enregistrer, à l’aide des cases à cocher de la boîte de dialogue **Renommer** qui apparaît en haut à droite de votre IDE.

1. Lorsque vous êtes satisfait de la modification, cliquez sur le bouton **Appliquer** ou appuyez sur **Entrée** pour valider les modifications.

> [!NOTE]
> Si vous utilisez un nom qui existe déjà, ce qui provoquerait un conflit, la boîte de dialogue **Renommer** dans votre IDE vous avertit.
>
> ![Conflit de changement de nom](media/rename-conflict-vb.png)

## <a name="see-also"></a>Voir aussi

[Refactorisation](../refactoring-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)