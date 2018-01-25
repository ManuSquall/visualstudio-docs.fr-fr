---
title: "Refactoriser un champ en une propriété dans C# | Microsoft Docs"
ms.custom: 
ms.date: 12/14/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vs.csharp.refactoring.encapsulatefield
dev_langs: csharp
ms.workload: dotnet
ms.openlocfilehash: 383f4e5bac2072b77d8e1d862cd4a1b859a57f7c
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="encapsulate-a-field-in-c"></a>Encapsuler un champ dans C# #

**Quoi :** vous permet de transformer un champ en une propriété et de mettre à jour toutes les utilisations de ce champ afin d’utiliser cette nouvelle propriété.

**Quand :** vous souhaitez déplacer un champ vers une propriété et mettre à jour toutes les références à ce champ.

**Pourquoi :** vous voulez donner à d’autres classes l’accès à un champ, mais ne souhaitez pas que ces classes dispose d’un accès direct.  En encapsulant le champ dans une propriété, vous pouvez écrire un code pour vérifier la valeur assignée, par exemple.

**Comment :**

1. Mettez en surbrillance ou placez le curseur de texte dans le nom du type à encapsuler :

   ![Code mis en surbrillance](media/encapsulate-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+R**, puis **Ctrl+E**.  (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez l’entrée **Encapsuler le champ** dans la fenêtre contextuelle d’aperçu.
   * **Souris**
     * Sélectionnez **Modifier > Refactoriser > Encapsuler le champ**.
     * Cliquez avec le bouton droit sur le code et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez l’entrée **Encapsuler le champ** dans la fenêtre contextuelle d’aperçu.

   Sélection | Description
   --------- | -----------
   **Encapsuler le champ (et utiliser la propriété)** | Encapsule le champ avec une propriété et met à jour toutes les utilisations du champ afin d’utiliser la propriété générée
   **Encapsuler le champ (mais utiliser toujours le champ)** | Encapsule le champ avec une propriété, mais conserve intactes toutes les utilisations de ce champ

   La propriété sera immédiatement créée et les références au champ seront mises à jour, le cas échéant.

   > [!TIP]
   > Utilisez le lien [**Aperçu des modifications**](../../ide/preview-changes.md) dans la fenêtre d’aperçu pour prévisualiser le résultat avant de le valider.

   ![Résultat de l’action Encapsuler une propriété](media/encapsulate-result-cs.png)

## <a name="see-also"></a>Voir aussi

[Refactorisation](../refactoring-in-visual-studio.md)  
[Aperçu des modifications](../../ide/preview-changes.md)