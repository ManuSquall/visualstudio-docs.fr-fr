---
title: "Déplacer un type vers un fichier correspondant - refactorisation (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 510b984ad2de9476d53e9a5a4bcd667f393d3d4b
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="move-type-to-a-matching-file-in-visual-basic"></a>Déplacer un type vers un fichier correspondant dans Visual Basic

**Quoi :** vous permet de déplacer le type sélectionné vers un fichier distinct portant le même nom.

**Quand :** vous avez plusieurs classes, structures, interfaces, etc. dans un même fichier et que vous souhaitez les séparer.  

**Pourquoi :** placer plusieurs types dans un même fichier peut ralentir la recherche de ces types.  En déplaçant les types vers des fichiers portant le même nom, le code devient plus lisible et cela facilite la navigation.

**Comment :**

1. Mettez en surbrillance ou placez le curseur de texte dans le nom du type à déplacer :

   ![Code mis en surbrillance](media/movetype-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl+.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer le type vers *TypeName*.vb** dans la fenêtre contextuelle d’aperçu, où *TypeName* est le nom du type que vous avez sélectionné.
   * **Souris**
     * Cliquez avec le bouton droit sur le code, choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Déplacer le type vers *TypeName*.vb** dans la fenêtre contextuelle d’aperçu, où *TypeName* est le nom du type que vous avez sélectionné.

   Le type sera aussitôt déplacé vers un nouveau fichier portant ce nom à l’intérieur de votre solution.

   ![Résultat de l’action Inclure](media/movetype-result-vb.png)

## <a name="see-also"></a>Voir aussi

[Refactorisation](../refactoring-in-visual-studio.md)