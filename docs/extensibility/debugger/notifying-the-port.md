---
title: "Notifier le Port | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ports, notification"
ms.assetid: f9fce48e-7d4e-4627-a0fb-77b75428146a
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Notifier le Port
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Après avoir lancé un programme, il doit être informé le port, comme suit :  
  
1.  Lorsqu'un port reçoit un nouveau nœud de programme, il envoie un événement de création de programme dans la session de débogage.  L'événement distribue à une interface qui représente le programme.  
  
2.  La session de débogage demande au programme pour l'identificateur d'un moteur \(DE\) de débogage vers lequel peut être attaché.  
  
3.  La session de débogage vérifie si le De est dans la liste DES autorisé pour ce programme.  La session de débogage reçoit cette liste des paramètres du programme actif de la solution, initialement passés à la procédure par le package de débogage.  
  
     Le De doit figurer sur la liste autorisée, ou bien le De ne sera pas joint au programme.  
  
 Par programme, lorsqu'un port reçoit d'abord un nouveau nœud de programme, il crée une interface d' [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) pour représenter le programme.  
  
> [!NOTE]
>  Cela ne doit pas être confondu avec l'interface d' `IDebugProgram2` créée ultérieurement par le moteur de \(DE\) débogage.  
  
 Le port envoie un événement de création du programme d' [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) vers le gestionnaire \(SDM\) de débogage de session au moyen d'une interface COM `IConnectionPoint` .  
  
> [!NOTE]
>  Cela ne doit pas être confondu avec l'interface d' `IDebugProgramCreateEvent2` , qui est envoyée ultérieurement par le De.  
  
 Avec l'interface d'événement lui\-même, le port envoie [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md), [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md), et les interfaces d' [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , qui représentent le port, fonctionnent, et des programmes, respectivement.  Le SDM appelle [IDebugProgram2 : : GetEngineInfo](../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md) pour obtenir le GUID du De qui peut mettre le programme.  GUID a été initialement fourni par l'interface d' [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) .  
  
 Le SDM vérifie si le De est dans la liste DES autorisé.  Le SDM reçoit cette liste des paramètres du programme actif de la solution, initialement passés à \-la par le package de débogage.  Le De doit figurer sur la liste autorisée, ou bien il ne sera pas joint au programme.  
  
 Une fois l'identité du De est connue, le SDM est prête à l'attacher au programme.  
  
## Voir aussi  
 [Lancement d'un programme](../../extensibility/debugger/launching-a-program.md)   
 [Attachement d'après le lancement d'un](../../extensibility/debugger/attaching-after-a-launch.md)   
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)