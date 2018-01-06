---
title: "Extraire la méthode - (refactorisation c#) | Documents Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: d79d55ae-f6bb-4902-8db2-e7fe01bdb0bf
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.extractmethod
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 44a5dd2da4cd19a532e8e6cc9f21ef48b2585fe4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="extract-a-method-in-c"></a>Extraire une méthode en c# #
**Ce que :** vous permet de transformer un fragment de code dans sa propre méthode.

**Quand :** vous avez un fragment de code existant dans une méthode qui doit être appelée à partir d’une autre méthode.  

**Pourquoi :** vous pouvez copier/coller ce code, mais cela entraîne la duplication.  Une meilleure solution consiste à refactoriser ce fragment dans sa propre méthode pouvant être appelée librement par toute autre méthode.

**Comment faire :**

1. Mettez en surbrillance le code à extraire :

   ![Code en surbrillance](media/extractmethod_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl + R**, puis **Ctrl + M**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **extraire la méthode** à partir du message de fenêtre d’aperçu.
   * **Souris**
     * Sélectionnez **Modifier > refactoriser > extraire la méthode**.
     * Le code d’avec le bouton droit et sélectionnez **refactoriser > Extraire > extraire la méthode**.
     * Cliquez sur le code, sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **extraire la méthode** à partir du message de fenêtre d’aperçu.

   La méthode est immédiatement créée.  À ce stade, vous pouvez maintenant renommer la méthode en tapant le nouveau nom.

   > [!TIP]
   > Vous pouvez également mettre à jour les commentaires et autres chaînes à utiliser ce nouveau nom, ainsi que [aperçu des modifications](../../ide/preview-changes.md) avant l’enregistrement, à l’aide des cases à cocher dans la **renommer** boîte qui apparaît en haut à droite de votre interface IDE.

   ![Renommer (méthode)](media/extractmethod_rename.png)

1. Lorsque vous êtes satisfait de la modification, cliquez sur le **appliquer** bouton ou appuyez sur **entrée** et les modifications sont validées.

## <a name="see-also"></a>Voir aussi  
[Refactorisation (C#)](../refactoring-csharp.md)  
[Aperçu des modifications](../../ide/preview-changes.md)