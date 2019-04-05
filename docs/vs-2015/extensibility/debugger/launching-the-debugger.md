---
title: Lancement du débogueur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4ae4c7eed2ae5477be02384ebe7b7c45383eaffb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938107"
---
# <a name="launching-the-debugger"></a>Lancement du débogueur
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lancement du débogueur nécessite l’envoi de la séquence des méthodes et des événements avec leurs attributs corrects.  
  
## <a name="sequences-of-methods-and-events"></a>Séquences de méthodes et événements  
  
1.  Le Gestionnaire de session de débogage (SDM) est appelé en choisissant le **déboguer** menu, puis en choisissant **Démarrer**. Consultez [lancement d’un programme](../../extensibility/debugger/launching-a-program.md) pour plus d’informations.  
  
2.  Les appels SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) (méthode).  
  
3.  Selon le modèle de processus de moteur (dé) de débogage, le `IDebugProgramNodeAttach2::OnAttach` méthode retourne une des méthodes suivantes, qui détermine ce qui se passe ensuite.  
  
     Si `S_FALSE` est retourné, le moteur de débogage (dé) doit être chargé en cours de la machine virtuelle.  
  
     - ou -  
  
     Si `S_OK` est retourné, l’Allemagne est chargé dans le processus du SDM. Le SDM effectue ensuite les tâches suivantes :  
  
    1.  Appels [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) pour obtenir les informations du moteur de l’Allemagne.  
  
    2.  Crée l’Allemagne.  
  
    3.  Appels [attacher](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  L’envoie DE un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) pour le SDM avec un `EVENT_SYNC` attribut.  
  
5.  L’envoie DE un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) pour le SDM avec un `EVENT_SYNC` attribut.  
  
6.  L’envoie DE un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) pour le SDM avec un `EVENT_SYNC` attribut.  
  
7.  L’envoie DE un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) pour le SDM avec un `EVENT_SYNC` attribut.  
  
8.  L’envoie DE un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) pour le SDM avec un `EVENT_SYNC` attribut.  
  
## <a name="see-also"></a>Voir aussi  
 [Appeler les événements de débogueur](../../extensibility/debugger/calling-debugger-events.md)   
 [Lancement d’un programme](../../extensibility/debugger/launching-a-program.md)
