---
title: Frames de pile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d38f53b6841c03e769c8d1f1af967cf903a0b32
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684090"
---
# <a name="stack-frames"></a>Frames de pile
Dans l’architecture du débogueur, une *frame de pile*:

-   Est une abstraction d’une pile qui fournit le contexte d’exécution d’un thread. Un thread s’exécute toujours dans une fonction. Un frame de pile conserve les variables locales de la fonction et les arguments. Pour déboguer avec Visual Studio, la langue ou l’environnement en cours de débogage doit prendre en charge les frames de pile.

-   Peut identifier et décrire lui-même et peut retourner le thread associé. Un frame de pile peut également retourner le contexte de code qui représente le pointeur d’instruction en cours et la documentation associée et des contextes d’évaluation d’expression.

-   A des propriétés qui décrivent le nom, le type et la valeur des variables locales et des arguments, et qui figurent dans les différentes fenêtres de débogage d’IDE.

-   Est représenté par un [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface, généralement créé par un moteur de débogage (dé) ou d’une machine virtuelle en raison de l’exécution d’un thread.

## <a name="see-also"></a>Voir aussi
- [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [Moteur de débogage](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)