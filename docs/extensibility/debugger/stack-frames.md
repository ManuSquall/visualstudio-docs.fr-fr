---
title: Cadres de pile Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ea79ad199e20afeb5d2bf1ca6a3cf881c6d51c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712841"
---
# <a name="stack-frames"></a>Piles de cadres
Dans l’architecture de débbugger, un *cadre de pile*:

- Est une abstraction d’une pile qui fournit le contexte d’exécution d’un fil. Un thread s’exécute toujours dans une fonction. Un cadre de pile détient les variables locales de la fonction et les arguments à elle. Afin de déboger avec Visual Studio, la langue ou l’environnement étant débogé doit soutenir les cadres de pile.

- Peut à la fois s’identifier et se décrire, et peut retourner le thread associé. Un cadre de pile peut également retourner le contexte du code qui représente le pointeur d’instruction actuel et les contextes associés d’évaluation de la documentation et de l’expression.

- A des propriétés qui décrivent le nom, le type et la valeur des variables et des arguments locaux, et qui apparaissent dans diverses fenêtres de débbug IDE.

- Est représenté par une interface [IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) généralement créée par un moteur de débogé (DE) ou une machine virtuelle à la suite de l’exécution d’un thread.

## <a name="see-also"></a>Voir aussi
- [Contextes Debugger](../../extensibility/debugger/debugger-contexts.md)
- [Concepts Debugger](../../extensibility/debugger/debugger-concepts.md)
- [Moteur Debug](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
