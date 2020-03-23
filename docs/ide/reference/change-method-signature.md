---
title: Changer la signature de la méthode
description: Supprimez ou modifiez l’ordre des paramètres d’une méthode. Cliquez avec le bouton droit sur la méthode, sélectionnez Actions rapides et refactorisations, puis sélectionnez Changer la signature.
ms.date: 01/26/2018
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 97c03c798732b5d722b2dc49f3ec7ffa490b4f06
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68711265"
---
# <a name="change-a-method-signature-refactoring"></a>Changer une signature de méthode (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de supprimer ou de modifier l’ordre des paramètres d’une méthode.

**Quand :** vous souhaitez déplacer ou supprimer un paramètre de méthode actuellement utilisé dans différents emplacements.

**Pourquoi :** vous pouvez manuellement supprimer et réorganiser les paramètres, puis rechercher tous les appels à cette méthode et les modifier un par un, mais cela peut entraîner des erreurs.  Cet outil de refactorisation effectuera automatiquement cette tâche.

## <a name="how-to"></a>Procédures

1. Mettez en surbrillance ou placez le curseur dans le nom de la méthode à modifier ou dans l’une de ses utilisations :

   - C# :

       ![Code C# mis en surbrillance](media/changesignature-highlight-cs.png)

   - VB :

       ![Code Visual Basic mis en surbrillance](media/changesignature-highlight-vb.png)

2. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
      - Appuyez sur **Ctrl+R**, puis **Ctrl+V**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
      - Appuyez **sur Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Modifier la signature** dans la fenêtre contextuelle d’aperçu.
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
   | **Restaurer** | Restaurer le paramètre barré sélectionné dans la liste

   > [!TIP]
   > Utilisez la case à **cocher des modifications de référence Preview** pour [voir quel sera le résultat](../../ide/preview-changes.md) avant de s’y engager.

4. Lorsque vous avez terminé, appuyez sur le bouton **OK** pour appliquer les modifications.

   - C# :

      ![Résultat du changement de la signature (C#)](media/changesignature-result-cs.png)

   - Visual Basic :

      ![Résultat du changement de la signature (Visual Basic)](media/changesignature-result-vb.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)