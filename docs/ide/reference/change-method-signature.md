---
title: "Refactoriser une signature de méthode dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: c181eb27ccdbc2f1efb7294e1610a6055245241c
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="change-a-method-signature-refactoring"></a>Changer une signature de méthode (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de supprimer ou de modifier l’ordre des paramètres d’une méthode.

**Quand :** vous souhaitez déplacer ou supprimer un paramètre de méthode actuellement utilisé dans différents emplacements.

**Pourquoi :** vous pouvez manuellement supprimer et réorganiser les paramètres, puis rechercher tous les appels à cette méthode et les modifier un par un, mais cela peut entraîner des erreurs.  Cet outil de refactorisation effectuera automatiquement cette tâche.

## <a name="how-to"></a>Procédure

1. Mettez en surbrillance ou placez le curseur dans le nom de la méthode à modifier ou dans l’une de ses utilisations :

   - C# :

    ![Code C# mis en surbrillance](media/changesignature-highlight-cs.png)

   - VB :

    ![Code Visual Basic mis en surbrillance](media/changesignature-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
     - Appuyez sur **Ctrl+R**, puis **Ctrl+V**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
     - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Modifier la signature** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
     - Sélectionnez **Modifier > Refactoriser > Supprimer les paramètres**.
     - Sélectionnez **Modifier > Refactoriser > Réorganiser les paramètres**.
     - Cliquez avec le bouton droit sur le code et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Modifier la signature** dans la fenêtre contextuelle d’aperçu.

1. Dans la boîte de dialogue **Modifier la signature** qui s’affiche, vous pouvez utiliser les boutons sur le côté droit pour modifier la signature de la méthode :

   ![Boîte de dialogue Modifier la signature](media/changesignature-dialog-cs.png)

   | Bouton | Description
   | ------ | ---
   | **Haut/bas** | Déplacer le paramètre sélectionné vers le haut ou le bas de la liste
   | **Supprimer**  | Supprimer le paramètre sélectionné de la liste
   | **Restauration** | Restaurer le paramètre barré sélectionné dans la liste

   > [!TIP]
   > Utilisez la case à cocher **Afficher un aperçu des modifications de la référence** pour [prévisualiser le résultat](../../ide/preview-changes.md) avant de le valider.

1. Lorsque vous avez terminé, appuyez sur le bouton **OK** pour appliquer les modifications.

   - C# :

    ![Résultat du changement de la signature (C#)](media/changesignature-result-cs.png)

   - Visual Basic :

    ![Résultat du changement de la signature (Visual Basic)](media/changesignature-result-vb.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)