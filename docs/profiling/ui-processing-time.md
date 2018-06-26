---
title: Temps de traitement de l’interface utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad48cd912bfdc117496bc9f876a1a2174e76dc04
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2018
ms.locfileid: "34477533"
---
# <a name="ui-processing-time"></a>Temps de traitement de l’IU
Ces segments de la chronologie sont associés à des périodes de blocage classées dans la catégorie Traitement de l’interface utilisateur. Ceci implique qu’un thread récupère les messages Windows ou exécute un autre travail lié à l’interface utilisateur. Pendant cette période, un thread a été bloqué dans une API, que le visualiseur concurrentiel considère comme étant du traitement de l’interface utilisateur. Les API comme `GetMessage()` et `MsgWaitForMultipleObjects()` appartiennent à ce groupe.  
  
 Si aucune API bloquante prédéfinie n’est identifiée, passez en revue les piles d’appels et les rapports de profil pour déterminer la cause sous-jacente du délai.  
  
 La catégorie Traitement de l’IU vous permet d’évaluer la réactivité des applications ayant une GUI. Elle est souhaitable dans les applications qui dépendent de la réactivité de l’IU. Par exemple, si le thread d’IU d’une application atteint 100 % du temps de traitement de l’IU, celle-ci est probablement très réactive. Cependant, si le thread d’interface utilisateur passe un temps considérable dans d’autres catégories, recherchez les causes racines et considérez les options permettant de réduire les catégories autre que Traitement de l’interface utilisateur sur ce thread.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)