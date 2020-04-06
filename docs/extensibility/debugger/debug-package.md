---
title: Forfait Debug (fr) Microsoft Docs
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
ms.openlocfilehash: de6240ea5d938d02f8415009203962e124ff049e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739019"
---
# <a name="debug-package"></a>Paquet Debug
Le paquet de débog s’exécute dans la coque Visual Studio et gère toute l’interface utilisateur. Il consomme les interfaces de débogage Visual Studio et communique avec le gestionnaire de déboguer de session (SDM).

 Pause événements envoyés à travers le commutateur SDM le débbugger du mode d’exécution en mode de rupture et de changer la mise au point au programme où la rupture s’est produite. Le paquet de débog suit le cadre et le fil de la pile à partir des informations qui lui sont envoyées par les événements.

 Le paquet de débaillement n’a pas de dépendances linguistiques ou d’environnement de temps d’exécution. Il n’est pas nécessaire d’implémenter ou de modifier le paquet de débogé.

 Le paquet de débaillement est implémenté par *vsdebug.dll*.

## <a name="see-also"></a>Voir aussi
- [Gestionnaire de débogé de session](../../extensibility/debugger/session-debug-manager.md)
- [Piles de cadres](../../extensibility/debugger/stack-frames.md)
- [Fils](../../extensibility/debugger/threads.md)
- [Composants Debugger](../../extensibility/debugger/debugger-components.md)
