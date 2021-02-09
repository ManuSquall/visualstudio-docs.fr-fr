---
title: Temps de traitement de l’interface utilisateur | Microsoft Docs
description: Découvrez que les segments de la chronologie sont associés à des temps de blocage catégorisés comme traitement de l’interface utilisateur.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 809af327fc2bb608647a76575736bd0e2b00c5b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922032"
---
# <a name="ui-processing-time"></a>Temps de traitement de l’IU
Ces segments de la chronologie sont associés à des périodes de blocage classées dans la catégorie Traitement de l’interface utilisateur. Ceci implique qu’un thread récupère les messages Windows ou exécute un autre travail lié à l’interface utilisateur. Pendant cette période, un thread a été bloqué dans une API, que le visualiseur concurrentiel considère comme étant du traitement de l’interface utilisateur. Les API comme `GetMessage()` et `MsgWaitForMultipleObjects()` appartiennent à ce groupe.

 Si aucune API bloquante prédéfinie n’est identifiée, passez en revue les piles d’appels et les rapports de profil pour déterminer la cause sous-jacente du délai.

 La catégorie Traitement de l’IU vous permet d’évaluer la réactivité des applications ayant une GUI. Elle est souhaitable dans les applications qui dépendent de la réactivité de l’IU. Par exemple, si le thread d’IU d’une application atteint 100 % du temps de traitement de l’IU, celle-ci est probablement très réactive. Cependant, si le thread d’interface utilisateur passe un temps considérable dans d’autres catégories, recherchez les causes racines et considérez les options permettant de réduire les catégories autre que Traitement de l’interface utilisateur sur ce thread.

## <a name="see-also"></a>Voir aussi
- [vue Threads](../profiling/threads-view-parallel-performance.md)