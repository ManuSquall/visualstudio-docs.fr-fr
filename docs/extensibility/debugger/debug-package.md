---
title: Déboguer le Package | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb843e63dbc4ff711b56ff457ca930dc9df0207
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010179"
---
# <a name="debug-package"></a>Déboguer le package
Le package de débogage s’exécute dans le shell Visual Studio et traite l’intégralité de l’interface utilisateur. Il consomme les interfaces de débogage Visual Studio et communique avec le Gestionnaire de session de débogage (SDM).  
  
 Événements d’arrêt envoyés via le SDM basculer le débogueur du mode exécution pour le mode arrêt et déplacer le focus vers le programme où l’arrêt s’est produit. Le package de débogage effectue le suivi de la frame de pile et thread à partir des informations qui lui sont envoyées par les événements.  
  
 Le package de débogage n’a aucune langue ou les dépendances de l’environnement d’exécution. Il n’est pas nécessaire d’implémenter ou de modifier le package de débogage.  
  
 Le package de débogage est implémenté par *vsdebug.dll*.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de session de débogage](../../extensibility/debugger/session-debug-manager.md)   
 [Frames de pile](../../extensibility/debugger/stack-frames.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)