---
title: Temps de traitement de l’interface utilisateur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bbed9d8c4725b6bd497377d4a9dee22f2f8573d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145484"
---
# <a name="ui-processing-time"></a>Temps de traitement UI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ces segments de la chronologie sont associés à des périodes de blocage classées dans la catégorie Traitement de l’interface utilisateur. Ceci implique qu’un thread récupère les messages Windows ou exécute un autre travail lié à l’interface utilisateur. Pendant cette période, un thread a été bloqué dans une API, que le visualiseur concurrentiel considère comme étant du traitement de l’interface utilisateur. Les API comme `GetMessage()` et `MsgWaitForMultipleObjects()` appartiennent à ce groupe.  
  
 Si aucune API bloquante prédéfinie n’est identifiée, passez en revue les piles d’appels et les rapports de profil pour déterminer la cause sous-jacente du délai.  
  
 La catégorie Traitement de l’interface utilisateur est importante pour comprendre la réactivité des applications avec une interface graphique, et elle est souhaitable dans les applications qui dépendent de la réactivité de l’interface utilisateur. Par exemple, si le thread d’interface utilisateur dans une application atteint 100 % du temps de traitement de l’interface utilisateur, elle est probablement très réactive. Cependant, si le thread d’interface utilisateur passe un temps considérable dans d’autres catégories, recherchez les causes racines et considérez les options permettant de réduire les catégories autre que Traitement de l’interface utilisateur sur ce thread.  
  
## <a name="see-also"></a>Voir aussi  
 [vue Threads](../profiling/threads-view-parallel-performance.md)
