---
title: Refactorisation de changement de-(Visual Basic) | Documents Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abf1565b-c7b7-4d45-b3d3-a438a836c70e
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.rename
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: da85803adf3de8afa0912a1f47e2b474952df51d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="rename-a-code-symbol-in-visual-basic"></a>Renommer un symbole de code en Visual Basic
**Ce que :** vous permet de renommer les identificateurs pour les symboles de code, tels que les champs, les variables locales, les méthodes, les espaces de noms, les propriétés et les types.

**Quand :** à quelque chose renommer en toute sécurité sans avoir à rechercher toutes les instances et copier/coller le nouveau nom.  

**Pourquoi :** en copiant et collant le nouveau nom dans un projet entier probablement entraîner des erreurs.  Cet outil refactorisation précisément effectue l’action de changement de nom.

**Comment faire :**

1. Mettez en surbrillance ou placez le curseur de texte à l’intérieur de l’élément à renommer :

   ![Code en surbrillance](media/rename_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl + R**, puis **Ctrl + R**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
   * **Souris**
     * Sélectionnez **Modifier > refactoriser > Renommer**.
     * Le code d’avec le bouton droit et sélectionnez **renommer**.

1. Renommer l’élément en tapant le nouveau nom.

   ![Renommer l’animation](media/rename_rename.png)

   > [!TIP]
   > Vous pouvez également mettre à jour les commentaires et autres chaînes à utiliser ce nouveau nom, ainsi que [aperçu des modifications](../../ide/preview-changes.md) avant l’enregistrement, à l’aide des cases à cocher dans la **renommer** boîte qui apparaît en haut à droite de votre interface IDE.

1. Lorsque vous êtes satisfait de la modification, cliquez sur le **appliquer** bouton ou appuyez sur **entrée** et les modifications sont validées.

> [!NOTE]
> Si vous utilisez un nom qui existe déjà, ce qui provoquerait un conflit, la **renommer** boîte dans votre IDE vous avertit.
>
> ![Renommer des conflits](media/rename_conflict.png)

## <a name="see-also"></a>Voir aussi  
[Refactorisation (Visual Basic)](../refactoring-vb.md)  
[Aperçu des modifications](../../ide/preview-changes.md)