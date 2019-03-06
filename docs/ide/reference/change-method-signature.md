---
title: Refactoriser la signature de la méthode
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 89af8235f897858094058981df52d6a3fec8a7d6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55934183"
---
# <a name="change-a-method-signature-refactoring"></a>Changer une signature de méthode (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** Vous permet de supprimer ou de modifier l’ordre des paramètres d’une méthode.

**Quand :** Vous souhaitez déplacer ou supprimer un paramètre de méthode actuellement utilisé dans différents emplacements.

**Pourquoi :** Vous pouvez manuellement supprimer et réorganiser les paramètres, puis rechercher tous les appels à cette méthode et les modifier un par un, mais cela peut entraîner des erreurs.  Cet outil de refactorisation effectuera automatiquement cette tâche.

## <a name="how-to"></a>Procédure

1. Mettez en surbrillance ou placez le curseur dans le nom de la méthode à modifier ou dans l’une de ses utilisations :

   - C# :

       ![Code C# mis en surbrillance](media/changesignature-highlight-cs.png)

   - VB :

       ![Code Visual Basic mis en surbrillance](media/changesignature-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl+R**, puis **Ctrl+V**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
      - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Modifier la signature** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
      - Sélectionnez **Modifier > Refactoriser > Supprimer les paramètres**.
      - Sélectionnez **Modifier > Refactoriser > Réorganiser les paramètres**.
      - Cliquez avec le bouton droit sur le code et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Modifier la signature** dans la fenêtre contextuelle d’aperçu.

3. Dans la boîte de dialogue **Modifier la signature** qui s’affiche, vous pouvez utiliser les boutons sur le côté droit pour modifier la signature de la méthode :

   ![Boîte de dialogue Modifier la signature](media/changesignature-dialog-cs.png)

   | Bouton | Description
   | ------ | ---
   | **Haut/bas** | Déplacer le paramètre sélectionné vers le haut ou le bas de la liste
   | **Supprimer** | Supprimer le paramètre sélectionné de la liste
   | **Restauration** | Restaurer le paramètre barré sélectionné dans la liste

   > [!TIP]
   > Utilisez la case à cocher **Afficher un aperçu des modifications de la référence** pour [prévisualiser le résultat](../../ide/preview-changes.md) avant de le valider.

4. Lorsque vous avez terminé, appuyez sur le bouton **OK** pour appliquer les modifications.

   - C# :

      ![Résultat du changement de la signature (C#)](media/changesignature-result-cs.png)

   - Visual Basic :

      ![Résultat du changement de la signature (Visual Basic)](media/changesignature-result-vb.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)