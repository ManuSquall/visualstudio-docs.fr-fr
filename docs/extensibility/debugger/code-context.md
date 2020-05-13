---
title: Contexte du code (en anglais seulement) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739153"
---
# <a name="code-context"></a>Contexte du code
Dans [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le débogage, un **contexte de code**:

- Fournit une abstraction d’une position dans le code connu du moteur de débogé (DE). Pour la plupart des architectures de temps d’exécution aujourd’hui, un contexte de code peut être considéré comme une adresse dans le flux d’instructions d’un programme. Pour les langues non traditionnelles, où le code peut ne pas être représenté par des instructions, un contexte de code peut être représenté par d’autres moyens.

- Décrit la position actuelle dans le flux d’exécution du programme que vous débogage.

- N’existe que lorsqu’un programme s’arrête à un point d’arrêt.

- A un contexte de document associé.

- Est implémenté par une interface [IDebugCodeContext2.](../../extensibility/debugger/reference/idebugcodecontext2.md)

## <a name="see-also"></a>Voir aussi
- [Contexte documentaire](../../extensibility/debugger/document-context.md)
- [Contextes Debugger](../../extensibility/debugger/debugger-contexts.md)
