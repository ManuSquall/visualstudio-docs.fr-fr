---
title: "Refactoriser une signature de méthode en C# | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 44aaf3f4a570600b715d6d54f5fd80da84611b94
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="change-a-method-signature-in-c"></a>Modifier une signature de méthode dans C# #

**Quoi :** vous permet de supprimer ou de modifier l’ordre des paramètres d’une méthode.

**Quand :** vous souhaitez déplacer ou supprimer un paramètre de méthode actuellement utilisé dans différents emplacements.  

**Pourquoi :** vous pouvez manuellement supprimer et réorganiser les paramètres, puis rechercher tous les appels à cette méthode et les modifier un par un, mais cela peut entraîner des erreurs.  Cet outil de refactorisation effectuera automatiquement cette tâche.

**Comment :**

1. Mettez en surbrillance ou placez le curseur dans le nom de la méthode à modifier ou dans l’une de ses utilisations :

   ![Code mis en surbrillance](media/changesignature-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+R**, puis **Ctrl+V**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Modifier la signature** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Sélectionnez **Modifier > Refactoriser > Supprimer les paramètres**.
     * Sélectionnez **Modifier > Refactoriser > Réorganiser les paramètres**.
     * Cliquez avec le bouton droit sur le code et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Modifier la signature** dans la fenêtre contextuelle d’aperçu.

1. Dans la boîte de dialogue **Modifier la signature** qui s’affiche, vous pouvez utiliser les boutons sur le côté droit pour modifier la signature de la méthode :

   ![Boîte de dialogue Modifier la signature](media/changesignature-dialog-cs.png)

   | Bouton | Description
   | ------ | ---
   | **Haut/bas** | Déplacer le paramètre sélectionné vers le haut ou le bas de la liste
   | **Supprimer**  | Supprimer le paramètre sélectionné de la liste
   | **Restauration** | Restaurer le paramètre barré sélectionné dans la liste

   > [!TIP]
   > Utilisez la case à cocher [**Afficher un aperçu des modifications de la référence**](../../ide/preview-changes.md) pour prévisualiser le résultat avant de le valider.

1. Lorsque vous avez terminé, appuyez sur le bouton **OK** pour appliquer les modifications.

   ![Résultat Modifier la signature](media/changesignature-result-cs.png)

## <a name="see-also"></a>Voir aussi

[Refactorisation](../refactoring-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)