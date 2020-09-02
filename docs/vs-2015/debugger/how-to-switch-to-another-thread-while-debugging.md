---
title: 'Comment : basculer vers un autre thread pendant le débogage | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 8f481a0b1cb2142dc7dbfe11e17ac627753cebf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176506"
---
# <a name="how-to-switch-to-another-thread-while-debugging"></a>Comment : basculer vers un autre thread pendant un débogage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous déboguez une application multithread, plusieurs méthodes s'offrent à vous pour remplacer le contexte du thread avec lequel vous travaillez par un autre thread.  
  
### <a name="to-switch-to-any-thread-that-appears-in-the-threads-window"></a>Pour basculer vers un thread figurant dans la fenêtre Threads  
  
- Double-cliquez sur le thread.  
  
### <a name="to-switch-to-a-thread-in-a-source-window"></a>Pour basculer vers un thread dans une fenêtre source  
  
- Dans la marge gauche, cliquez avec le bouton droit sur un indicateur de thread, pointez sur **basculer vers**, puis cliquez sur le nom du thread vers lequel vous souhaitez basculer. Le menu contextuel contient uniquement les threads de cet emplacement spécifique.  
  
     Si aucun indicateur n’apparaît, cliquez avec le bouton droit dans la fenêtre **Threads** et vérifiez que l’option **afficher les threads dans la source** est sélectionnée.  
  
### <a name="to-switch-to-a-thread-in-the-debug-location-toolbar"></a>Pour basculer vers un thread dans la barre d'outils Emplacement de débogage  
  
1. Dans la barre d’outils **emplacement de débogage** , cliquez sur la zone **thread** .  
  
2. Dans la liste, cliquez sur le thread vers lequel vous souhaitez basculer.  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
