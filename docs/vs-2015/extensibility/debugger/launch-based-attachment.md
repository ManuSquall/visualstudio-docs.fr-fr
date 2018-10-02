---
title: Pièce jointe basée sur le lancement | Microsoft Docs
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
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e52e364e49bb38e6be812edec9f5fa5d8f26df0f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501110"
---
# <a name="launch-based-attachment"></a>Pièce jointe basée sur le lancement
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [basée sur le lancement de pièce jointe](https://docs.microsoft.com/visualstudio/extensibility/debugger/launch-based-attachment).  
  
En fonction du lancement de pièce jointe à un programme est automatique. Lorsque le processus qui héberge le programme est lancé par le SDM, basée sur le lancement de pièce jointe suit un chemin d’accès semblable à celle de la méthode manuelle de pièce jointe. Pour plus d’informations, consultez [attacher au programme](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Le processus d’attachement  
 La principale différence est la séquence d’événements suivant le **attacher** appeler, comme suit :  
  
1.  Envoyer un **IDebugEngineCreateEvent2** objet d’événement pour le SDM. Pour plus d’informations, consultez [envoi des événements](../../extensibility/debugger/sending-events.md).  
  
2.  Appelez le `IDebugProgram2::GetProgramId` méthode sur le **IDebugProgram2** interface passé à la **attacher** (méthode).  
  
3.  Envoyer un **IDebugProgramCreateEvent2** objet d’événement pour avertir le SDM qui local **IDebugProgram2** objet a été créé pour représenter le programme pour l’Allemagne.  
  
4.  Envoyer un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) objet d’événement pour avertir le SDM qu’un nouveau thread est créé pour le processus lancé.  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi des événements requis](../../extensibility/debugger/sending-the-required-events.md)   
 [Activation d’un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

