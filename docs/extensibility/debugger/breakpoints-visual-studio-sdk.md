---
title: Points d’arrêt (Kit de développement logiciel Visual Studio) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c353ca11df1a897ec5dc8acecd822c1c1f44e92
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707027"
---
# <a name="breakpoints-visual-studio-sdk"></a>Points d’arrêt (SDK Visual Studio)
Il existe trois types de points d’arrêt : en attente, la limite et d’erreur.

 **Un en attente de point d’arrêt :**

- Est une abstraction qui contient toutes les informations nécessaires pour lier un point d’arrêt à un ou plusieurs contextes de code dans un ou plusieurs programmes. Chaque fois qu’un programme débogué code cause à charger, le moteur de débogage qui consulte des tous les points d’arrêt en attente pour voir si elles peuvent être liées.

   Un point d’arrêt en attente lui-même jamais lie au code, mais plutôt collecte et est dit qu’il contient tous les points d’arrêt les liés qu’il génère.

- Est représenté par un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interface.

  **Un point d’arrêt lié :**

- Est une abstraction pour un point d’arrêt associée ou liée à un contexte de code unique. Chaque point d’arrêt lié est généré en réponse à un point d’arrêt en attente. Un point d’arrêt en attente peut, toutefois, générer plus d’un point d’arrêt lié.

   Lorsque le code est déchargé, un point d’arrêt lié peut être indépendant et ignorée.

- Est représenté par un [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interface.

  **Un point d’arrêt de l’erreur :**

- Est une abstraction pour la description d’une erreur dans la tentative de liaison d’un point d’arrêt en attente à un contexte de code. Un point d’arrêt de l’erreur décrit une erreur dans l’emplacement ou dans l’expression de point d’arrêt lui-même. Pour plus d’informations, consultez [liaison des points d’arrêt](../../extensibility/debugger/binding-breakpoints.md).

   L’erreur de point d’arrêt peut être une erreur ou un avertissement.

- Est représenté par un [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interface.

## <a name="see-also"></a>Voir aussi
- [Programmes](../../extensibility/debugger/programs.md)
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [Contexte de code](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)