---
title: Déboguer le Package | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dda8b1ac6eaa2cd5352d441600ae720c3aac321c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181294"
---
# <a name="debug-package"></a>Déboguer le package
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le package de débogage s’exécute dans le shell Visual Studio et traite l’intégralité de l’interface utilisateur. Il consomme les interfaces de débogage Visual Studio et communique avec le Gestionnaire de session de débogage (SDM).  
  
 Événements d’arrêt envoyés via le SDM basculer le débogueur du mode exécution pour le mode arrêt et déplacer le focus vers le programme où l’arrêt s’est produit. Le package de débogage effectue le suivi de la frame de pile et thread à partir des informations qui lui sont envoyées par les événements.  
  
 Le package de débogage n’a aucune langue ou les dépendances de l’environnement d’exécution. Il n’est pas nécessaire d’implémenter ou de modifier le package de débogage.  
  
 Le package de débogage est implémenté par vsdebug.dll.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de session de débogage](../../extensibility/debugger/session-debug-manager.md)   
 [Frames de pile](../../extensibility/debugger/stack-frames.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)
