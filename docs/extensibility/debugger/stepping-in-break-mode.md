---
title: Passer en mode Pause (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3161fc1c1ec8b44d96b3793198ac630ba2e32d67
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712855"
---
# <a name="stepping-in-break-mode"></a>Passer en mode pause
La section suivante décrit le processus qui se produit lorsque le débbuggeur est en mode pause et doit passer par le code :

## <a name="stepping-process"></a>Processus d’étape

1. Appelez [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) with [STEPKIND](../../extensibility/debugger/reference/stepkind.md) et [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) arguments to execute a step.

2. Lorsque l’étape est terminée, envoyez un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) comme un événement d’arrêt.

## <a name="see-also"></a>Voir aussi
- [Appel d’événements débbugger](../../extensibility/debugger/calling-debugger-events.md)
