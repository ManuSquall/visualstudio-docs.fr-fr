---
title: Pas à pas détaillé en mode arrêt | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712855"
---
# <a name="stepping-in-break-mode"></a>Exécution pas à pas en mode arrêt
La section suivante décrit le processus qui se produit lorsque le débogueur est en mode arrêt et doit exécuter le code pas à pas :

## <a name="stepping-process"></a>Processus d’exécution pas à pas

1. Appelez [IDebugProgram2 :: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) avec [STEPKIND](../../extensibility/debugger/reference/stepkind.md) et [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) arguments pour exécuter une étape.

2. Lorsque l’étape est terminée, envoyez un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) en tant qu’événement d’arrêt.

## <a name="see-also"></a>Voir aussi
- [Appel des événements du débogueur](../../extensibility/debugger/calling-debugger-events.md)
