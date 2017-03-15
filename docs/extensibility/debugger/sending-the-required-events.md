---
title: "Envoyer les &#233;v&#233;nements requis | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "événements de demande de débogage (débogage SDK),"
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Envoyer les &#233;v&#233;nements requis
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

utilisez cette procédure pour envoyer des événements requis.  
  
## Processus d'envoi d'événements requis  
 Les événements suivants sont nécessaires, dans cet ordre, en créant un moteur de débogage \(DE\) et en les joignant à un programme :  
  
1.  Envoyez un objet événement d' [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) au gestionnaire de débogage de session \(SDM\) lorsque le De est initialisée pour déboguer un ou plusieurs programmes dans un processus.  
  
2.  Lorsque le programme à déboguer est attaché, envoyez un objet événement d' [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) au SDM.  Cet événement peut être un événement arrêtant, selon votre conception du moteur.  
  
3.  Si le programme est attaché lorsque le processus est lancé, envoyez un objet événement d' [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) au SDM pour informer l'IDE de le nouveau thread.  Cet événement peut être un événement arrêtant, selon votre conception du moteur.  
  
4.  Envoyez un objet événement d' [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) au SDM lorsque le programme débogué est le chargement terminé ou lorsque la jointure au programme est terminé.  Cet événement doit être un événement arrêtant.  
  
5.  Si l'application à déboguer est lancée, envoyez un objet événement d' [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) au SDM lorsque la première instruction de code dans l'architecture au moment de l'exécution est sur le point d'être exécutée.  Cet événement est toujours un événement arrêtant.  En faisant \- pas détaillé dans la session de débogage, l'IDE s'arrête à cet événement.  
  
> [!NOTE]
>  De nombreux langages utilisent les initialiseurs globaux ou les fonctions externes et précompilé \(de la bibliothèque CRT ou du \_Main\) au début de leur code.  Si le langage du programme que vous déboguez contient l'une ou l'autre de ces types d'éléments avant le point d'entrée initiale, ce code est exécuté et l'événement point d'entrée est envoyé lorsque le point d'entrée d'utilisateur, comme **principal** ou `WinMain`, est atteint.  
  
## Voir aussi  
 [L'activation d'un programme à déboguer](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)