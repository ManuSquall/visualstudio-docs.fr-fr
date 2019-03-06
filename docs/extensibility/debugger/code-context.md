---
title: Contexte de code | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 65e4d37a-086b-426e-9394-a3534967fd59
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 114537976561e72a9b1922c41d94ffa5e7ce613b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714542"
---
# <a name="code-context"></a>Contexte de code
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] débogage, un **contexte de code**:

-   Fournit une abstraction d’une position dans le code comme connu du moteur de débogage (dé). Pour la plupart des architectures d’exécution dès aujourd'hui, un contexte de code peut être considéré comme une adresse dans le flux d’instructions d’un programme. Pour les langues non traditionnel, où code ne peut pas être représenté par des instructions, un contexte de code peut être représenté par d’autres moyens.

-   Décrit la position actuelle dans le flux d’exécution du programme que vous déboguez.

-   Existe uniquement lorsqu’un programme s’est arrêté à un point d’arrêt.

-   A un contexte de document associé.

-   Est implémentée par un [IDebugCodeContext2](../../extensibility/debugger/reference/idebugcodecontext2.md) interface.

## <a name="see-also"></a>Voir aussi
- [Contexte de document](../../extensibility/debugger/document-context.md)
- [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md)