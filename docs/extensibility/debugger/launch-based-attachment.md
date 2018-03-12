---
title: "Pièce jointe de lancement | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d05f0b8d8fd0190391da831351b65d873eac4efc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="launch-based-attachment"></a>Pièce jointe de lancement
Basé sur le lancement de pièce jointe à un programme est automatique. Lorsque le processus qui héberge le programme est lancé par le SDM, pièce jointe de lancement suit un chemin d’accès semblable à celle de la méthode d’attachement manuel. Pour plus d’informations, consultez [au programme](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Le processus d’attachement  
 La principale différence est la séquence d’événements suit le **attacher** appeler, comme suit :  
  
1.  Envoyer un **IDebugEngineCreateEvent2** objet d’événement pour le SDM. Pour plus d’informations, consultez [envoyer des événements](../../extensibility/debugger/sending-events.md).  
  
2.  Appelez le `IDebugProgram2::GetProgramId` méthode sur le **IDebugProgram2** interface est passée à la **attacher** (méthode).  
  
3.  Envoyer un **IDebugProgramCreateEvent2** objet d’événement pour avertir le SDM qui local **IDebugProgram2** objet a été créé pour représenter le programme à le DE.  
  
4.  Envoyer un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) objet d’événement pour avertir le SDM qu’un nouveau thread est créé pour le processus qui a lancé.  
  
## <a name="see-also"></a>Voir aussi  
 [Envoyer les événements requis](../../extensibility/debugger/sending-the-required-events.md)   
 [Activation d’un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)