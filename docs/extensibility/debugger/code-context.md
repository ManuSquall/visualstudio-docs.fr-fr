---
title: Contexte de code | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6424c1182f30b1bbfe6c166209b94afb7ec45549
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739153"
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
