---
title: "Déplacer un type vers un fichier correspondant - refactorisation (C#) | Microsoft Docs"
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
ms.workload: dotnet
ms.openlocfilehash: 4b7b9b1ba52bed5d2bdf042db0149d799c489a7d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="move-a-type-to-a-matching-file-in-c"></a>Déplacer un type vers un fichier correspondant dans C# #

**Quoi :** vous permet de déplacer le type sélectionné vers un fichier distinct portant le même nom.

**Quand :** vous avez plusieurs classes, structures, interfaces, etc. dans un même fichier et que vous souhaitez les séparer.

**Pourquoi :** placer plusieurs types dans un même fichier peut ralentir la recherche de ces types.  En déplaçant les types vers des fichiers portant le même nom, le code devient plus lisible et cela facilite la navigation.

**Comment :**

1. Mettez en surbrillance ou placez le curseur de texte dans le nom du type à déplacer :

   ![Code mis en surbrillance](media/movetype-highlight-cs.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer le type vers *TypeName*.cs** dans la fenêtre contextuelle d’aperçu, où *TypeName* est le nom du type que vous avez sélectionné.
   * **Souris**
     * Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer le type vers *TypeName*.cs** dans la fenêtre contextuelle d’aperçu, où *TypeName* est le nom du type que vous avez sélectionné.

   Le type sera aussitôt déplacé vers un nouveau fichier portant ce nom à l’intérieur de votre solution.

   ![Résultat de l’action Inclure](media/movetype-result-cs.png)

## <a name="see-also"></a>Voir aussi

[Refactorisation](../refactoring-in-visual-studio.md)