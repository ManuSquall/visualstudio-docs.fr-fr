---
title: 'Comment : Rechercher un thread dans la vue threads | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5974bc962faf439af8de5d50bf51bad3d824647
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "91838494"
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Comment : rechercher un thread dans la vue Threads
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez rechercher un thread spécifique dans la vue threads en utilisant son ID de thread ou sa chaîne de module comme critère de recherche. Vous pouvez également spécifier le sens initial de la recherche. Les champs de la boîte de dialogue affichent les attributs du thread sélectionné dans l’arborescence des threads.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Pour rechercher un thread dans la vue threads  
  
1. Réorganisez vos fenêtres de manière à ce que Spy + + et une fenêtre [vue threads](../debugger/threads-view.md) active soient visibles.  
  
2. Dans le menu **Rechercher** , choisissez **Rechercher un thread**.  
  
    La [boîte de dialogue recherche de thread](../debugger/thread-search-dialog-box.md) s’ouvre.  
  
3. Tapez l’ID de thread ou une chaîne de module en tant que critères de recherche.  
  
4. Effacez tous les champs pour lesquels vous ne souhaitez pas spécifier de valeurs.  
  
   > [!TIP]
   > Pour rechercher tous les threads appartenant à un module, désactivez la zone de texte **thread** et tapez le nom du module dans la zone **module** . Ensuite, utilisez **Rechercher suivant** pour poursuivre la recherche de threads.  
  
5. Choisissez **haut** ou **bas** pour la direction initiale de la recherche.  
  
6. Cliquez sur **OK**.  
  
   Si un thread correspondant est trouvé, il est mis en surbrillance dans la fenêtre vue threads.
