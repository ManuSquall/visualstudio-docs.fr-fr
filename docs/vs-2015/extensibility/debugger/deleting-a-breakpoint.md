---
title: Suppression d’un point d’arrêt | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18b88cc55a4c641e56c062356a9f74c2224835a8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47504524"
---
# <a name="deleting-a-breakpoint"></a>Suppression d’un point d’arrêt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [suppression d’un point d’arrêt](https://docs.microsoft.com/visualstudio/extensibility/debugger/deleting-a-breakpoint).  
  
La section suivante décrit le processus lors de la suppression d’un point d’arrêt en attente :  
  
## <a name="deletion-process"></a>Processus de suppression  
 Le Gestionnaire de session de débogage (SDM) appelle le [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) méthode pour supprimer le point d’arrêt en attente et les points d’arrêt liés liée à partir de celui-ci.  
  
> [!NOTE]
>  Un seul point d’arrêt lié peut également être supprimée par un appel à [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements d’appel du débogueur](../../extensibility/debugger/calling-debugger-events.md)

