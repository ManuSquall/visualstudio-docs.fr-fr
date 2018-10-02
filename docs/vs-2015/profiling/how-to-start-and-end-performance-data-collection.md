---
title: Guide pratique pour démarrer et terminer la collecte des données de performances | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.wizard.summarypage
helpviewer_keywords:
- profiling tools, launching sessions
- performance sessions, launching
- performance sessions, ending
- profiling tools, ending sessions
ms.assetid: 9f6eb0d5-d9e9-4bec-b627-445065610bce
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7c7848f8bb45ae9c97dacdd75c42e8345646e5f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506881"
---
# <a name="how-to-start-and-end-performance-data-collection"></a>Guide pratique pour démarrer et terminer la collecte des données de performances
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : Démarrer et collecte de données de performances de fin](https://docs.microsoft.com/visualstudio/profiling/how-to-start-and-end-performance-data-collection).  
  
Vous devez ajouter le fichier binaire cible à profiler à la session de performance avant de démarrer le profilage. Pour ajouter une cible, cliquez avec le bouton droit sur **Cibles** dans l’**Explorateur de performances**, puis cliquez sur **Ajouter un fichier binaire cible**. Dans la boîte de dialogue **Ajouter un fichier binaire cible**, sélectionnez le nom du fichier, puis cliquez sur **Ouvrir**. Un nouveau fichier binaire est ajouté.  
  
### <a name="to-start-profiling"></a>Pour démarrer le profilage  
  
1.  Cliquez avec le bouton droit sur le nom de la session de performance dans la fenêtre **Explorateur de performances**, puis choisissez l’une des options suivantes :  
  
    -   **Démarrer avec le profilage** : démarre l’application et commence immédiatement le profilage.  
  
    -   **Démarrer avec le profilage suspendu** : démarre l’application sans commencer le profilage. Pour commencer le profilage, sélectionnez **Reprendre la collecte** dans la fenêtre **Contrôle de collecte de données**. Pour plus d’informations, consultez [Guide pratique pour suspendre et reprendre la collecte de données de performances](../profiling/how-to-pause-and-resume-performance-data-collection.md).  
  
### <a name="to-end-profiling"></a>Pour terminer le profilage  
  
-   Pour terminer une session de profilage, il est recommandé de quitter l’application. Pour arrêter immédiatement le profilage, dans la barre d’outils de l’**Explorateur de performances**, cliquez sur **Arrêter**.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôle de la collecte de données](../profiling/controlling-data-collection.md)   
 [Guide pratique pour suspendre et reprendre la collecte de données de performances](../profiling/how-to-pause-and-resume-performance-data-collection.md)


