---
title: "Signature de méthode de modification - (refactorisation c#) | Documents Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: b4f45f9d-9c8f-46ae-99f7-7705c6d90b6e
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs: csharp
ms.openlocfilehash: 9ed72704c37fcfc5d0c48ba17937f5b06097ce0b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="change-a-method-signature-in-c"></a>Modifier une signature de méthode en c# #
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
[Refactorisation (C#)](../refactoring-csharp.md)  
[Aperçu des modifications](../../ide/preview-changes.md)