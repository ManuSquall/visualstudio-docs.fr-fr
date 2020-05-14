---
title: Points d’arrêt (Visual Studio SDK) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c9d61c82886f237e8c9f544a59d8fe167548277
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739192"
---
# <a name="breakpoints-visual-studio-sdk"></a>Points d’arrêt (SDK Visual Studio)
Il existe trois types de points d’arrêt : en attente, lié et erreur.

 **Un point d’arrêt en attente:**

- Est une abstraction qui contient toutes les informations nécessaires pour lier un point d’arrêt à un ou plusieurs contextes de code dans un ou plusieurs programmes. Chaque fois qu’un programme étant déboché cause le code de charge, le moteur de débog vérifie tous les points de rupture en attente pour voir si elles peuvent être liées.

   Un point d’arrêt en attente lui-même ne se lie jamais au code, mais plutôt recueille et est dit de contenir tous les points de rupture liés qu’il génère.

- Est représenté par une interface [IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

  **Un point d’arrêt lié :**

- Est une abstraction pour un point d’arrêt associé à ou lié à un contexte de code unique. Chaque point d’arrêt lié est généré en réponse à un point d’arrêt en attente. Un point d’arrêt en attente peut cependant générer plus d’un point d’arrêt lié.

   Lorsque le code est déchargé, un point de rupture lié peut être délimité et jeté.

- Est représenté par une interface [IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

  **Un point d’erreur :**

- Est une abstraction pour décrire une erreur en essayant de lier un point d’arrêt en attente à un contexte de code. Un point d’erreur décrit soit une erreur dans l’emplacement, soit dans l’expression du point d’arrêt lui-même. Pour plus d’informations, voir [points d’arrêt contraignants](../../extensibility/debugger/binding-breakpoints.md).

   L’erreur de point d’arrêt peut être soit une erreur, soit un avertissement.

- Est représenté par une interface [IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

## <a name="see-also"></a>Voir aussi
- [Programmes](../../extensibility/debugger/programs.md)
- [Concepts Debugger](../../extensibility/debugger/debugger-concepts.md)
- [Contexte du code](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
