---
title: Exécution pas à pas en Mode arrêt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eb7b7e847c116f3aab38a12ec9801988bb8b3fc1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60111543"
---
# <a name="stepping-in-break-mode"></a>Exécution pas à pas en mode arrêt
La section suivante décrit le processus qui se produit lorsque le débogueur est en mode arrêt et qu’il doit parcourir le code :

## <a name="stepping-process"></a>Procédure pas à pas

1. Appelez [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) avec [STEPKIND](../../extensibility/debugger/reference/stepkind.md) et [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) arguments d’exécuter une étape.

2. Lorsque l’étape est terminée, envoyer un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) comme un événement d’arrêt.

## <a name="see-also"></a>Voir aussi
- [Appel des événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)