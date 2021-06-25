---
title: Frames de pile | Microsoft Docs
description: Cet article décrit la définition et le rôle d’un frame de pile dans l’architecture du débogueur dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- stack frames, debugging
- debugging [Debugging SDK], stack frames
- stack frames
ms.assetid: b5e439d4-1e9d-4e13-9cad-bb8b136d4ca8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 77b503afcc38ab9427e5268097655433007de5d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898550"
---
# <a name="stack-frames"></a>Frames de pile
Dans l’architecture du débogueur, un *Frame de pile*:

- Est une abstraction d’une pile qui fournit le contexte d’exécution d’un thread. Un thread s’exécute toujours dans une fonction. Un frame de pile contient les variables locales de la fonction et les arguments qu’il contient. Pour déboguer avec Visual Studio, le langage ou l’environnement en cours de débogage doit prendre en charge les frames de pile.

- Peut à la fois identifier et décrire lui-même, et peut retourner le thread associé. Un frame de pile peut également retourner le contexte de code qui représente le pointeur d’instruction actuel et la documentation et les contextes d’évaluation d’expression associés.

- A des propriétés qui décrivent le nom, le type et la valeur des variables locales et des arguments, et qui s’affichent dans différentes fenêtres de débogage IDE.

- Est représenté par une interface [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , généralement créée par un moteur de débogage (de) ou un ordinateur virtuel suite à l’exécution d’un thread.

## <a name="see-also"></a>Voir aussi
- [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [Moteur de débogage](../../extensibility/debugger/debug-engine.md)
- [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md)
