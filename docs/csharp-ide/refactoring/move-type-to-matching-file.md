---
title: "Déplacer le type de fichier correspondant - (refactorisation c#) | Documents Microsoft"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40f58c34-c50f-4297-91b2-2e243380dcc9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9fa5a15f9c8e688c973594309efbfa6cb5d10e8b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="move-a-type-to-a-matching-file-in-c"></a>Déplacer un type dans un fichier correspondant dans le langage c# #
**Ce que :** vous permet de déplacer le type sélectionné dans un fichier distinct portant le même nom.

**Quand :** vous avez plusieurs classes, structures, interfaces, etc. dans le même fichier auquel vous souhaitez séparer.  

**Pourquoi :** placer plusieurs types dans le même fichier peut rendre difficile la recherche de ces types.  En déplaçant les types de fichiers portant le même nom, le code devient plus lisible et plus facile d’accéder.

**Comment faire :**

1. Mettez en surbrillance ou placez le curseur de texte dans le nom du type à déplacer :

   ![Code en surbrillance](media/movetype_highlight.png)

1. Ensuite, effectuez l’une des opérations suivantes :
   * **Clavier**
     * Appuyez sur **Ctrl +.** pour déclencher le **Actions rapides et refactorisations** menu et sélectionnez **déplacer type *TypeName*.cs** à partir de la fenêtre de la fenêtre Aperçu, où *TypeName* est le nom du type que vous avez sélectionné.
   * **Souris**
     * Cliquez sur le code, sélectionnez le **Actions rapides et refactorisations** menu et sélectionnez **déplacer type *TypeName*.cs** à partir de la fenêtre de la fenêtre Aperçu, où  *TypeName* est le nom du type que vous avez sélectionné.

   Le type sera instantanément déplacé vers un nouveau fichier avec ce nom à l’intérieur de votre solution.

   ![Résultats inline](media/movetype_result.png)

## <a name="see-also"></a>Voir aussi  
[Refactorisation (C#)](../refactoring-csharp.md)