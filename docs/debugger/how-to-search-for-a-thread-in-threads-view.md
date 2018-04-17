---
title: 'Comment : rechercher un Thread dans la vue Threads | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- threads, searching
ms.assetid: 5609a9b3-c279-4426-9e2e-dd87896a6d6f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2d582a10e2738b69724765477ee64c47e8cb68c3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-search-for-a-thread-in-threads-view"></a>Comment : rechercher un thread dans la vue Threads
Vous pouvez rechercher un thread spécifique dans la vue Threads à l’aide de sa chaîne de module ou d’ID de thread comme critère de recherche. Vous pouvez également spécifier la direction initiale de la recherche. Les champs dans la boîte de dialogue affiche les attributs du thread sélectionné dans l’arborescence des threads.  
  
### <a name="to-search-for-a-thread-in-threads-view"></a>Pour rechercher un thread dans la vue Threads  
  
1.  Fenêtres ainsi que Spy ++ et qu’une [vue Threads](../debugger/threads-view.md) fenêtre sont visibles.  
  
2.  À partir de la **recherche** menu, choisissez **rechercher le Thread**.  
  
     Le [boîte de dialogue de recherche de Thread](../debugger/thread-search-dialog-box.md) s’ouvre.  
  
3.  Tapez l’ID de thread ou une chaîne de module comme critère de recherche.  
  
4.  Désactivez tous les champs pour lesquels vous ne souhaitez pas spécifier de valeurs.  
  
    > [!TIP]
    >  Pour rechercher tous les threads détenus par un module, désactivez le **Thread** nom de zone de texte et le type du module dans la **Module** boîte. Utilisez ensuite **suivant** pour poursuivre la recherche pour les threads.  
  
5.  Choisissez **des** ou **vers le bas** pour la direction initiale de la recherche.  
  
6.  Cliquez sur **OK**.  
  
 Si un thread correspondant est trouvé, il est mis en surbrillance dans la fenêtre de la vue Threads.