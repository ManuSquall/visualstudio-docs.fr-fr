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
ms.openlocfilehash: b1d1e587fa7e089ee3c137ffa836a99d31dd62f8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="ui-processing-time"></a>Temps de traitement UI
Ces segments de la chronologie sont associés à des périodes de blocage classées dans la catégorie Traitement de l’interface utilisateur. Ceci implique qu’un thread récupère les messages Windows ou exécute un autre travail lié à l’interface utilisateur. Pendant cette période, un thread a été bloqué dans une API, que le visualiseur concurrentiel considère comme étant du traitement de l’interface utilisateur. Les API comme `GetMessage()` et `MsgWaitForMultipleObjects()` appartiennent à ce groupe.  
  
 Si aucune API bloquante prédéfinie n’est identifiée, passez en revue les piles d’appels et les rapports de profil pour déterminer la cause sous-jacente du délai.  
  
 La catégorie Traitement de l’interface utilisateur est importante pour comprendre la réactivité des applications avec une interface graphique, et elle est souhaitable dans les applications qui dépendent de la réactivité de l’interface utilisateur. Par exemple, si le thread d’interface utilisateur dans une application atteint 100 % du temps de traitement de l’interface utilisateur, elle est probablement très réactive. Cependant, si le thread d’interface utilisateur passe un temps considérable dans d’autres catégories, recherchez les causes racines et considérez les options permettant de réduire les catégories autre que Traitement de l’interface utilisateur sur ce thread.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue Threads](../profiling/threads-view-parallel-performance.md)