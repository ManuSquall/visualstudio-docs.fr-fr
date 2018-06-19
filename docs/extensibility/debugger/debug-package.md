---
title: Déboguer le Package | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6ca438b7ed8c9b6a4b84693f975144040f998f01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110027"
---
# <a name="debug-package"></a>Déboguer le Package
Le package de débogage s’exécute dans le shell Visual Studio et gère l’ensemble de l’interface utilisateur. Il consomme les interfaces de débogage Visual Studio et communique avec le Gestionnaire de session de débogage (SDM).  
  
 Événements d’arrêt envoyés via le SDM basculer le débogueur du mode exécution pour le mode arrêt et déplacer le focus vers le programme où l’arrêt s’est produit. Le package de débogage effectue le suivi de la frame de pile et d’un thread à partir des informations qui lui sont envoyées par les événements.  
  
 Le package de débogage n’a aucun langage ou les dépendances de l’environnement d’exécution. Il n’est pas nécessaire d’implémenter ou de modifier le package de débogage.  
  
 Le package de débogage est implémenté par vsdebug.dll.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestionnaire de session de débogage](../../extensibility/debugger/session-debug-manager.md)   
 [Frames de pile](../../extensibility/debugger/stack-frames.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)