---
title: 'Comment : Pg préc ou vers le bas dans la mémoire | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, paging up or down in memory
- memory, paging up or down
- Disassembly window, viewing memory space
- Memory window, paging up or down in memory
ms.assetid: 50b30a68-66f6-43f8-a48b-59ce12c95471
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f49664edc622c9944015c4cea9814a7deb2cfe7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292680"
---
# <a name="how-to-page-up-or-down-in-memory"></a>Comment : se déplacer d'une page vers le haut ou vers le bas dans la mémoire
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous affichez le contenu de la mémoire dans un **mémoire** fenêtre ou le **désassemblage** fenêtre, vous pouvez utiliser la barre de défilement verticale pour faire monter ou Descendre dans l’espace de mémoire.  
  
### <a name="to-page-up-or-down-in-memory"></a>Pour vous déplacer d'une page vers le haut ou vers le bas dans la mémoire  
  
1.  Pour vous déplacer d'une page vers le bas (atteindre une adresse mémoire supérieure), cliquez dans la barre de défilement verticale au-dessous de la case de défilement.  
  
2.  Pour vous déplacer d'une page vers le haut (atteindre une adresse mémoire inférieure), cliquez dans la barre de défilement verticale au-dessus du curseur.  
  
 Remarquez que la barre de défilement verticale ne se comporte pas de manière habituelle. L'espace adresse d'un ordinateur moderne est très importante, et il serait facile de se perdre en faisant glisser le curseur de défilement vers un emplacement aléatoire. Pour cette raison, le curseur est « fixé » et reste toujours au milieu de la barre de défilement. Dans les applications en code natif, vous pouvez vous déplacer d'une page vers le haut ou vers le bas, mais il est impossible de défiler librement.  
  
 Dans les applications managées, le désassemblage se limitant à une fonction, vous pouvez utiliser le défilement normal.  
  
 Remarquez que l'adresse la plus haute est affichée en bas de la fenêtre. Pour afficher une adresse plus haute, vous devez descendre et non pas monter.  
  
#### <a name="to-move-up-or-down-one-instruction"></a>Pour monter ou descendre d'une instruction  
  
-   Cliquez sur la flèche en haut ou en bas de la barre de défilement vertical.  
  
## <a name="see-also"></a>Voir aussi  
 [Mémoire Windows](../debugger/memory-windows.md)   
 [Comment : utiliser la fenêtre code machine](../debugger/how-to-use-the-disassembly-window.md)   
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)





