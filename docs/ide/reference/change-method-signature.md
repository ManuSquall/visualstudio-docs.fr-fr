---
title: Changer la signature de la méthode
description: Ajoutez, supprimez ou modifiez l’ordre des paramètres d’une méthode. Cliquez avec le bouton droit sur la méthode, sélectionnez Actions rapides et refactorisations, puis sélectionnez Changer la signature.
ms.date: 07/20/2020
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
ms.openlocfilehash: 2d91406b65950515afb3659c0d5918841465b2fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86869566"
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
      - Appuyez sur **CTRL** + **.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Modifier la signature** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
      - Sélectionnez **Modifier > Refactoriser > Supprimer les paramètres**.
      - Sélectionnez **Modifier > Refactoriser > Réorganiser les paramètres**.
      - Cliquez avec le bouton droit sur le code et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Modifier la signature** dans la fenêtre contextuelle d’aperçu.

3. Dans la boîte de dialogue **Modifier la signature** qui s’affiche, vous pouvez utiliser les boutons sur le côté droit pour modifier la signature de la méthode :

   ![Boîte de dialogue Modifier la signature](media/change-signature.png)

   | Bouton | Description
   | ------ | ---
   | **Haut/bas** | Déplacer le paramètre sélectionné vers le haut ou le bas de la liste
   | **Ajouter** | Ajouter un nouveau paramètre à la liste
   | **Remove** | Supprimer le paramètre sélectionné de la liste
   | **Restauration** | Restaurer le paramètre barré sélectionné dans la liste

   > [!TIP]
   > Utilisez la case à cocher **aperçu des modifications** de la référence pour [Voir le résultat](../../ide/preview-changes.md) avant de le valider.

4. Si vous sélectionnez **Ajouter** dans la boîte de dialogue **modifier la signature** , la boîte de dialogue **Ajouter un paramètre** s’ouvre. La boîte de dialogue **Ajouter un paramètre** vous permet d’ajouter un nom de type et un nom de paramètre. Vous pouvez choisir de rendre le paramètre obligatoire ou facultatif avec une valeur par défaut. Vous pouvez ensuite ajouter une valeur au site d’appel et choisir un argument nommé pour cette valeur, ou vous pouvez introduire une variable TODO. La variable TODO place un TODO dans votre code afin que vous puissiez consulter chaque erreur et parcourir indépendamment chaque site d’appel, puis décider de ce qui doit être transmis. Pour les paramètres facultatifs, vous avez la possibilité d’omettre complètement le site d’appel.

    ![Boîte de dialogue Ajouter un paramètre-C #](media/add-parameter-dialog.png)

5. Lorsque vous avez terminé d’ajouter un paramètre, cliquez sur **OK** pour afficher un aperçu des modifications.

    ![Boîte de dialogue Modifier la signature](media/change-signature.png)

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)