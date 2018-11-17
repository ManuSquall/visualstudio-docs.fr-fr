---
title: 'Comment : basculer vers un autre Thread pendant un débogage | Microsoft Docs'
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
helpviewer_keywords:
- threads, switching [debugging]
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad13c81afc82ac69055ae117c862a1cf73b51478
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737709"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>Comment : basculer vers un autre thread pendant un débogage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous déboguez une application multithread, plusieurs méthodes s'offrent à vous pour remplacer le contexte du thread avec lequel vous travaillez par un autre thread.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>Pour basculer vers un thread figurant dans la fenêtre Threads  
  
-   Double-cliquez sur le thread.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Pour basculer vers un thread dans une fenêtre source  
  
-   Dans la marge de gauche, cliquez sur un indicateur de thread, pointez sur **basculer vers**, puis cliquez sur le nom du thread auquel vous souhaitez basculer. Le menu contextuel contient uniquement les threads de cet emplacement spécifique.  
  
     Si aucun indicateur n’apparaît, avec le bouton droit dans le **Threads** fenêtre et vérifiez que **afficher les Threads dans la Source** est sélectionné.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Pour basculer vers un thread dans la barre d'outils Emplacement de débogage  
  
1.  Sur le **emplacement de débogage** barre d’outils, cliquez sur le **Thread** boîte.  
  
2.  Dans la liste, cliquez sur le thread vers lequel vous souhaitez basculer.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)



