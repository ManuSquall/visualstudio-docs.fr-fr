---
title: 'Procédure : Page précédente ou suivante en mémoire | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b8452100eb744d019c0f4c8d5e62566ac761210
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072746"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Procédure : Se déplacer d’une page vers le haut ou vers le bas dans la mémoire

Quand vous affichez le contenu de la mémoire dans la fenêtre **Mémoire** ou **Code Machine**, vous pouvez vous servir de la barre de défilement verticale pour vous déplacer dans l’espace mémoire.

### <a name="to-page-up-or-down-in-memory"></a>Pour vous déplacer d'une page vers le haut ou vers le bas dans la mémoire

1. Pour vous déplacer d'une page vers le bas (atteindre une adresse mémoire supérieure), cliquez dans la barre de défilement verticale au-dessous de la case de défilement.

2. Pour vous déplacer d'une page vers le haut (atteindre une adresse mémoire inférieure), cliquez dans la barre de défilement verticale au-dessus du curseur.

   Remarquez que la barre de défilement verticale ne se comporte pas de manière habituelle. L'espace adresse d'un ordinateur moderne est très importante, et il serait facile de se perdre en faisant glisser le curseur de défilement vers un emplacement aléatoire. Pour cette raison, le curseur est « fixé » et reste toujours au milieu de la barre de défilement. Dans les applications en code natif, vous pouvez vous déplacer d'une page vers le haut ou vers le bas, mais il est impossible de défiler librement.

   Dans les applications managées, le désassemblage se limitant à une fonction, vous pouvez utiliser le défilement normal.

   Remarquez que l'adresse la plus haute est affichée en bas de la fenêtre. Pour afficher une adresse plus haute, vous devez descendre et non pas monter.

#### <a name="to-move-up-or-down-one-instruction"></a>Pour monter ou descendre d'une instruction

- Cliquez sur la flèche en haut ou en bas de la barre de défilement vertical.

## <a name="see-also"></a>Voir aussi
- [Fenêtres Mémoire](../debugger/memory-windows.md)
- [Guide pratique pour utiliser la fenêtre Code Machine](../debugger/how-to-use-the-disassembly-window.md)
- [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)