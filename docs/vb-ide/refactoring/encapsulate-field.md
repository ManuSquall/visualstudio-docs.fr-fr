---
title: Encapsuler le champ - refactorisation (Visual Basic) | Documents Microsoft
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: VB
ms.assetid: 39a9ed11-363f-4dda-af3b-0affe6db1d42
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.encapsulatefield
dev_langs: VB
ms.openlocfilehash: 9575ad83ead4960016ba7814642cacb1db04ea4d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="encapsulate-a-field-in-visual-basic"></a>Encapsuler un champ en Visual Basic
**Ce que :** vous permet de transformer un champ d’une propriété et mettre à jour toutes les utilisations de ce champ pour utiliser la propriété nouvellement créée.

**Quand :** vous souhaitez déplacer un champ dans une propriété et mettre à jour toutes les références à ce champ.  

**Pourquoi :** afin de donner l’accès des autres classes à un champ, mais vous ne souhaitez pas que ces classes d’avoir un accès direct.  En encapsulant le champ dans une propriété, vous pouvez écrire du code pour vérifier que la valeur assignée, par exemple.

**Comment faire :**

1. Mettez en surbrillance ou placez le curseur de texte dans le nom du champ à encapsuler :

   ![Code en surbrillance](media/encapsulate_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl + R**, puis **Ctrl + E**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **encapsuler le champ** entrée à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Sélectionnez **Modifier > refactoriser > encapsuler le champ**.
     * Cliquez sur le code, sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **encapsuler le champ** entrée à partir du message de fenêtre d’aperçu.

   Sélection | Description
   --------- | -----------
   **Encapsuler le champ (et utiliser la propriété)** | Encapsule le champ avec une propriété et met à jour toutes les utilisations du champ à utiliser la propriété générée
   **Encapsuler le champ (mais utiliser toujours le champ)** | Encapsule le champ avec une propriété, mais conserve toutes les utilisations du champ intact

   Créer immédiatement la propriété et les références au champ seront mise à jour, si activée.

   > [!TIP]
   > Utilisez le [ **aperçu des modifications** ](../../ide/preview-changes.md) lien dans la fenêtre contextuelle pour voir quels seront le résultats avant de les utiliser.

   ![Encapsuler le résultat de propriété](media/encapsulate_result.png)

## <a name="see-also"></a>Voir aussi  
[Refactorisation (Visual Basic)](../refactoring-vb.md)  
[Aperçu des modifications](../../ide/preview-changes.md)