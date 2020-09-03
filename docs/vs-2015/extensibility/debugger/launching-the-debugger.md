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
ms.openlocfilehash: e9c57079246dd52bd7fb44371999d0c3747dad40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149128"
---
# <a name="launching-the-debugger"></a>Lancement du débogueur
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le lancement du débogueur nécessite l’envoi de la séquence correcte des méthodes et des événements avec leurs attributs appropriés.  
  
## <a name="sequences-of-methods-and-events"></a>Séquences de méthodes et d’événements  
  
1. Le gestionnaire de débogage de session (SDM) est appelé en choisissant le menu **Déboguer** , puis en sélectionnant **Démarrer**. Pour plus d’informations, consultez [lancement d’un programme](../../extensibility/debugger/launching-a-program.md) .  
  
2. Le SDM appelle la méthode [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .  
  
3. Selon le modèle DE processus du moteur DE débogage (DE), la `IDebugProgramNodeAttach2::OnAttach` méthode retourne l’une des méthodes suivantes, qui détermine ce qui se passe ensuite.  
  
     Si `S_FALSE` est retourné, le moteur de débogage doit être chargé en cours de traitement de l’ordinateur virtuel.  
  
     - ou -  
  
     Si `S_OK` est retourné, le de doit être chargé dans le processus du SDM. Le SDM effectue ensuite les tâches suivantes :  
  
    1. Appelle [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) pour récupérer les informations du moteur de.  
  
    2. Co-crée le DE.  
  
    3. Appelle [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4. Le DE envoie un [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) au SDM avec un `EVENT_SYNC` attribut.  
  
5. Le DE envoie un [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) au SDM avec un `EVENT_SYNC` attribut.  
  
6. Le DE envoie un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) au SDM avec un `EVENT_SYNC` attribut.  
  
7. Le DE envoie un [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) au SDM avec un `EVENT_SYNC` attribut.  
  
8. Le DE envoie un [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) au SDM avec un `EVENT_SYNC` attribut.  
  
## <a name="see-also"></a>Voir aussi  
 [Appel des événements du débogueur](../../extensibility/debugger/calling-debugger-events.md)   
 [Lancement d’un programme](../../extensibility/debugger/launching-a-program.md)
