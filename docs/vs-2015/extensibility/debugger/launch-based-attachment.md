---
title: Pièce jointe basée sur le lancement | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09a6b39bef9ba6af098bf92d779a490e22492209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203165"
---
# <a name="launch-based-attachment"></a>Pièce jointe basée sur le lancement
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La pièce jointe basée sur le lancement d’un programme est automatique. Lorsque le processus hébergeant le programme est lancé par le SDM, la pièce jointe basée sur le lancement suit un chemin d’accès similaire à celui de la méthode manuelle des pièces jointes. Pour plus d’informations, consultez [attachement au programme](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Processus d’attachement  
 La principale différence est la séquence d’événements qui suivent l’appel d' **attachement** , comme suit :  
  
1. Envoie un objet d’événement **IDebugEngineCreateEvent2** au SDM. Pour plus d’informations, consultez [envoi d’événements](../../extensibility/debugger/sending-events.md).  
  
2. Appelez la `IDebugProgram2::GetProgramId` méthode sur l’interface **IDebugProgram2** transmise à la méthode **Attach** .  
  
3. Envoie un objet d’événement **IDebugProgramCreateEvent2** pour notifier au SDM que l’objet **IDebugProgram2** local a été créé pour représenter le programme au de.  
  
4. Envoie un objet d’événement [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) pour notifier au SDM qu’un nouveau thread est créé pour le processus qui a été lancé.  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi des événements requis](../../extensibility/debugger/sending-the-required-events.md)   
 [Activation d’un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
