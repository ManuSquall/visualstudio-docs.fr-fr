---
title: Pas à pas détaillé en mode arrêt | Microsoft Docs
description: En savoir plus sur le processus qui se produit lorsque le débogueur est en mode arrêt. Le débogueur doit ensuite effectuer un pas à pas détaillé dans le code.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0ed11d05e4351ac6ba76bc9aa10531a8a96ddf23
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075404"
---
# <a name="stepping-in-break-mode"></a>Exécution pas à pas en mode arrêt
La section suivante décrit le processus qui se produit lorsque le débogueur est en mode arrêt et doit exécuter le code pas à pas :

## <a name="stepping-process"></a>Processus d’exécution pas à pas

1. Appelez [IDebugProgram2 :: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) avec [STEPKIND](../../extensibility/debugger/reference/stepkind.md) et [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) arguments pour exécuter une étape.

2. Lorsque l’étape est terminée, envoyez un [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) en tant qu’événement d’arrêt.

## <a name="see-also"></a>Voir aussi
- [Appel des événements du débogueur](../../extensibility/debugger/calling-debugger-events.md)
