---
title: Package de débogage | Microsoft Docs
description: Découvrez comment le package de débogage s’exécute dans le shell Visual Studio et gère l’interface utilisateur en consommant les interfaces de débogage et en communiquant avec le gestionnaire de débogage de session.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90c4c82895f7a30d4df9126a280c6c9ffa7ffa76
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067905"
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
