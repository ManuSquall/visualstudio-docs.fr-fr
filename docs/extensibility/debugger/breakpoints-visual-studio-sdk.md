---
title: Points d’arrêt (kit de développement logiciel Visual Studio) | Microsoft Docs
description: 'En savoir plus sur les trois types de points d’arrêt : en attente, lié et erreur. Cet article répertorie les interfaces utilisées pour implémenter les types.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1fce472faf95aa77f87ab02d78a3da640b6bd3bf
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901485"
---
# <a name="breakpoints-visual-studio-sdk"></a>Points d’arrêt (SDK Visual Studio)
Il existe trois types de points d’arrêt : en attente, lié et erreur.

 **Un point d’arrêt en attente :**

- Est une abstraction qui contient toutes les informations nécessaires pour lier un point d’arrêt à un ou plusieurs contextes de code dans un ou plusieurs programmes. Chaque fois qu’un programme en cours de débogage provoque le chargement du code, le moteur de débogage vérifie tous les points d’arrêt en attente pour voir s’ils peuvent être liés.

   Un point d’arrêt en attente lui-même n’est jamais lié au code, mais il est considéré comme contenant tous les points d’arrêt liés qu’il génère.

- Est représenté par une interface [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

  **Point d’arrêt lié :**

- Est une abstraction pour un point d’arrêt associé ou lié à un contexte de code unique. Chaque point d’arrêt lié est généré en réponse à un point d’arrêt en attente. Toutefois, un point d’arrêt en attente peut générer plusieurs points d’arrêt liés.

   Lorsque le code est déchargé, un point d’arrêt lié peut être indépendant et ignoré.

- Est représenté par une interface [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

  **Un point d’arrêt d’erreur :**

- Est une abstraction pour décrire une erreur lors de la tentative de liaison d’un point d’arrêt en attente à un contexte de code. Un point d’arrêt d’erreur décrit une erreur dans l’emplacement ou dans l’expression de point d’arrêt proprement dite. Pour plus d’informations, consultez [liaison de points d’arrêt](../../extensibility/debugger/binding-breakpoints.md).

   L’erreur de point d’arrêt peut être une erreur ou un avertissement.

- Est représenté par une interface [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .

## <a name="see-also"></a>Voir aussi
- [Programmes](../../extensibility/debugger/programs.md)
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [Contexte de code](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
