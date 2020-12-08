---
title: Frames de pile | Microsoft Docs
description: Cet article décrit la définition et le rôle d’un frame de pile dans l’architecture du débogueur dans Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ab2c891002ad90d767a4c5ca9efffd3f3d1d10ee
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845204"
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
