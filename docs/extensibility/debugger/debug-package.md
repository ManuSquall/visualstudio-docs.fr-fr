---
title: Package de débogage | Microsoft Docs
description: Découvrez comment le package de débogage s’exécute dans le shell Visual Studio et gère l’interface utilisateur en consommant les interfaces de débogage et en communiquant avec le gestionnaire de débogage de session.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad62a487d38500617999a276aa3ae15a75089736
ms.sourcegitcommit: 8e9c38da7bcfbe9a461c378083846714933a0e1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96914125"
---
# <a name="debug-package"></a>Package de débogage
Le package de débogage s’exécute dans le shell Visual Studio et gère toute l’interface utilisateur. Il consomme les interfaces de débogage de Visual Studio et communique avec le gestionnaire de débogage de session (SDM).

 Arrêter les événements envoyés via le commutateur SDM le débogueur du mode exécution au mode arrêt et changer le focus du programme où l’arrêt s’est produit. Le package de débogage effectue le suivi du frame de pile et du thread à partir des informations qui lui sont envoyées par les événements.

 Le package de débogage n’a pas de dépendances d’environnement de langage ou d’exécution. Il n’est pas nécessaire d’implémenter ou de modifier le package de débogage.

 Le package de débogage est implémenté par *vsdebug.dll*.

## <a name="see-also"></a>Voir aussi
- [Gestionnaire de débogage de session](../../extensibility/debugger/session-debug-manager.md)
- [Frames de pile](../../extensibility/debugger/stack-frames.md)
- [Threads](../../extensibility/debugger/threads.md)
- [Composants du débogueur](../../extensibility/debugger/debugger-components.md)
