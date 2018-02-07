---
title: "Extraire une méthode dans Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: f9e55a41f9a61626e8fce18cb11da6edc8a8bced
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2018
---
# <a name="extract-a-method-in-visual-basic"></a>Extraire une méthode dans Visual Basic

**Quoi :** vous permet de transformer un fragment de code dans sa propre méthode.

**Quand :** vous avez un fragment de code existant dans une méthode qui doit être appelée à partir d’une autre méthode.  

**Pourquoi :** vous pouvez copier/coller ce code, mais cela entraîne une duplication.  Une meilleure solution consiste à refactoriser ce fragment dans sa propre méthode pouvant être appelée librement par toute autre méthode.

**Comment :**

1. Mettez en surbrillance le code à extraire :

   ![Code mis en surbrillance](media/extractmethod-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+R**, puis **Ctrl+M**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire la méthode** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Sélectionnez **Modifier > Refactoriser > Extraire la méthode**.
     * Cliquez avec le bouton droit sur le code, puis sélectionnez **Refactoriser > Extraire > Extraire la méthode**.
     * Cliquez avec le bouton droit sur le code et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire la méthode** dans la fenêtre contextuelle d’aperçu.

   La méthode sera immédiatement créée.  À partir d’ici, il vous suffit de taper le nouveau nom de la méthode pour la renommer.

   > [!TIP]
   > Vous pouvez également mettre à jour les commentaires et autres chaînes afin d’utiliser ce nouveau nom, et [afficher un aperçu des modifications](../../ide/preview-changes.md) avant de les enregistrer, à l’aide des cases à cocher de la boîte de dialogue **Renommer** qui apparaît en haut à droite de votre IDE.

   ![Renommer la méthode](media/extractmethod-rename-vb.png)

1. Lorsque vous êtes satisfait de la modification, cliquez sur le bouton **Appliquer** ou appuyez sur **Entrée** pour valider les modifications.

## <a name="see-also"></a>Voir aussi

[Refactorisation](../refactoring-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)