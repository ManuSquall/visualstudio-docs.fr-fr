---
title: "Bas&#233; sur le lancement de pi&#232;ce jointe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "moteurs de débogage, lancement"
  - "moteurs de débogage, attacher aux programmes"
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Bas&#233; sur le lancement de pi&#232;ce jointe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

la pièce jointe Lancement\-basée à un programme est automatique.  Lorsque l'hébergement de processus le programme est exécuté par le SDM, la pièce jointe lancement\-basée suit un chemin d'accès similaire à celui de la méthode manuelle de pièce jointe.  Pour plus d'informations, consultez l' [Attachement au programme](../../extensibility/debugger/attaching-to-the-program.md).  
  
## Le processus attachement  
 La différence principale est la séquence d'événements suivant l'appel d' **Attacher** , comme suit :  
  
1.  envoyez un objet événement d' **IDebugEngineCreateEvent2** au SDM.  Pour plus d'informations, consultez l' [événements d'émission](../../extensibility/debugger/sending-events.md).  
  
2.  appelez la méthode d' `IDebugProgram2::GetProgramId` sur l'interface d' **IDebugProgram2** passée à la méthode d' **Attacher** .  
  
3.  envoyez un objet événement d' **IDebugProgramCreateEvent2** pour informer le SDM que l'objet local d' **IDebugProgram2** a été créé pour représenter le programme au De.  
  
4.  Envoyez un objet événement d' [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) pour informer le SDM qu'un thread est créé pour le processus qui a lancé.  
  
## Voir aussi  
 [Envoyer les événements requis](../../extensibility/debugger/sending-the-required-events.md)   
 [L'activation d'un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)