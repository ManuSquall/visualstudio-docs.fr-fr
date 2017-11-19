---
title: "Comment : basculer vers un autre Thread pendant un débogage | Documents Microsoft"
ms.custom: 
ms.date: 04/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14432de4519ed49292810af5f96399bbf87e43cd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-switch-to-another-thread-while-debugging-in-visual-studio"></a>Comment : basculer vers un autre Thread pendant un débogage dans Visual Studio
Lorsque vous déboguez une application multithread, vous pouvez utiliser l’une des méthodes pour basculer à partir du thread que vous avez travaillé avec vers un autre thread.

> [!NOTE]
> Si vous souhaitez contrôler l’ordre dans lequel les threads exécutent, vous devez [figer et libérer les threads](/debugger/get-started-debugging-multithreaded-apps.md).

Lorsque vous examinez les threads dans l’éditeur de code et les différentes fenêtres de débogage multithreads, la flèche jaune indique que le thread actuel. Une flèche verte avec extrémité recourbée indique qu’un thread non actuel possède le contexte du débogueur.
  
### <a name="to-switch-to-any-thread-that-appears"></a>Pour basculer vers n’importe quel thread qui s’affiche 
  
-   Dans le **Threads** ou **espion parallèle** fenêtre, double-cliquez sur le thread.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Pour basculer vers un thread dans une fenêtre source  
  
-   Dans la marge de gauche, cliquez sur une icône de marqueur de thread ![marqueur de Thread](../debugger/media/dbg-thread-marker.png "ThreadMarker"), pointez sur **basculer vers**, puis cliquez sur le nom du thread vers lequel vous souhaitez basculer . Le menu contextuel contient uniquement les threads de cet emplacement spécifique.  
  
     Si aucun marqueur de thread n’apparaît, avec le bouton droit dans le **Threads** fenêtre et vérifiez que **afficher les Threads dans la Source** est sélectionnée.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Pour basculer vers un thread dans la barre d'outils Emplacement de débogage  
  
1.  Sur le **emplacement de débogage** barre d’outils, cliquez sur le **Thread** liste.  
  
2.  Dans la liste, cliquez sur le thread vers lequel vous souhaitez basculer.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)