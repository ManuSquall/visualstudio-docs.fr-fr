---
title: Contexte de code | Microsoft Docs
description: En savoir plus sur le contexte de code dans le débogage Visual Studio, qui décrit une position dans le code qui existe lorsqu’un programme s’est arrêté à un point d’arrêt.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3e3bd252990e52f4ecaede0cc5026067b28434bc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905720"
---
# <a name="code-context"></a>Contexte de code
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le cadre du débogage, un **contexte de code**:

- Fournit une abstraction d’une position dans le code telle que connue du moteur de débogage (DE). Pour la plupart des architectures Runtime actuelles, un contexte de code peut être considéré comme une adresse dans le flux d’instructions d’un programme. Pour les langages non traditionnels, où le code ne peut pas être représenté par des instructions, un contexte de code peut être représenté par d’autres moyens.

- Décrit la position actuelle dans le flux d’exécution du programme que vous déboguez.

- Existe uniquement lorsqu’un programme s’est arrêté à un point d’arrêt.

- A un contexte de document associé.

- Est implémenté par une interface [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) .

## <a name="see-also"></a>Voir aussi
- [Contexte de document](../../extensibility/debugger/document-context.md)
- [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)
