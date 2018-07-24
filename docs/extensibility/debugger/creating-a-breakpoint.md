---
title: Création d’un point d’arrêt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, creating
- debugging [Debugging SDK], creating breakpoints
ms.assetid: 6f9f87bb-192e-45e0-9a7a-ffe729e87f7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04eefdca7459f95da3ddef0430a59f9af52e581e
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39203899"
---
# <a name="create-a-breakpoint"></a>Créer un point d’arrêt
La section suivante décrit le processus de création d’un point d’arrêt.  
  
## <a name="methods-in-breakpoint-creation"></a>Méthodes de création de point d’arrêt  
 Lorsque le module qui est nécessaire pour lier un point d’arrêt est chargé, le Gestionnaire de session de débogage (SDM) appelle les méthodes suivantes :  
  
1.  [IDebugPendingBreakpoint2::Enable](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)  
  
2.  [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)  
  
3.  [IDebugPendingBreakpoint2::CanBind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)  
  
    > [!NOTE]
    >  **CanBind** est appelée uniquement lorsqu’un utilisateur effectue un point d’arrêt à partir de la **des points d’arrêt** fenêtre.  
  
4.  [IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)  
  
5.  [IDebugPendingBreakpoint2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Appeler des événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)