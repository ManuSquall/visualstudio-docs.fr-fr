---
title: Création d’un point d’arrêt | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7cde6d660506e05195ef9f5c0825845cee10ae5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839698"
---
# <a name="creating-a-breakpoint"></a>Création d’un point d’arrêt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Les éléments suivants décrivent le processus de création d’un point d’arrêt.  
  
## <a name="methods-in-breakpoint-creation"></a>Méthodes de création de point d’arrêt  
 Lorsque le module nécessaire pour lier un point d’arrêt est chargé, le gestionnaire de débogage de session (SDM) appelle les méthodes suivantes :  
  
1. [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)  
  
2. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)  
  
3. [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)  
  
    > [!NOTE]
    > **CanBind** est appelé uniquement lorsqu’un utilisateur crée un point d’arrêt à partir de la fenêtre points d’arrêt.  
  
4. [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)  
  
5. [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)
