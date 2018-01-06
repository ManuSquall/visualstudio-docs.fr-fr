---
title: "Changement de signature de méthode - refactorisation (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 64b37bca-92b8-4154-9d65-54073e5740fc
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs: VB
ms.workload: multiple
ms.openlocfilehash: ac0b8394f71f2f7949cf21b4ea34eba733bf4d34
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="change-a-method-signature-in-visual-basic"></a>Modifier une signature de méthode dans Visual Basic
**Ce que :** vous permet de supprimer ou modifier l’ordre des paramètres d’une méthode.

**Quand :** vous souhaitez déplacer ou supprimer un paramètre de méthode qui est actuellement utilisé dans différents emplacements.  

**Pourquoi :** vous pourriez manuellement supprimer et réorganiser les paramètres, puis rechercher tous les appels à cette méthode et les modifier une par une, mais qui peut entraîner des erreurs.  Cet outil refactorisation effectuera automatiquement la tâche.

**Comment faire :**

1. Mettez en surbrillance ou placez le curseur de texte dans le nom de la méthode permettant de modifier ou de l’un de ses utilisations :

   ![Code en surbrillance](media/changesignature_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl + R**, puis **Ctrl + V**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **changement de Signature** à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Sélectionnez **Modifier > refactoriser > Supprimer les paramètres**.
     * Sélectionnez **Modifier > refactoriser > Réorganiser les paramètres**.
     * Cliquez sur le code, sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **changement de Signature** à partir du message de fenêtre d’aperçu.

1. Dans le **modifier la Signature** boîte de dialogue qui s’affiche, vous pouvez utiliser les boutons sur le côté droit pour modifier la signature de méthode :

   ![Modifiez la boîte de dialogue Signature](media/changesignature_dialog.png)

   | Bouton | Description
   | ------ | ---
   | **Haut/bas** | Déplacer le paramètre sélectionné en haut et bas de la liste
   | **Supprimer**  | Supprimez le paramètre sélectionné dans la liste
   | **Restauration** | Restaurer le paramètre sélectionné, barré à la liste

   > [!TIP]
   > Utilisez le [ **aperçu des modifications de référence** ](../../ide/preview-changes.md) case à cocher pour voir quels seront le résultats avant de les utiliser.

1. Lorsque vous avez terminé, appuyez sur la **OK** bouton apporter les modifications.

   ![Modifier le résultat de la Signature](media/changesignature_result.png)

## <a name="see-also"></a>Voir aussi  
[Refactorisation (Visual Basic)](../refactoring-vb.md)  
[Aperçu des modifications](../../ide/preview-changes.md)