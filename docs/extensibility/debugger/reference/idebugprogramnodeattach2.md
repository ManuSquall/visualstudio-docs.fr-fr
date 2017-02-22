---
title: "IDebugProgramNodeAttach2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNodeAttach2"
helpviewer_keywords: 
  - "Interface de IDebugProgramNodeAttach2"
ms.assetid: 46b37ac9-a026-4ad3-997b-f19e2f8deb73
caps.latest.revision: 3
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 3
---
# IDebugProgramNodeAttach2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Permet un nœud de programme de telle sorte qu'il soit notifié d'une tentative de s'attacher au programme associé.  
  
## Syntaxe  
  
```  
IDebugProgramNodeAttach2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Cette interface est implémentée sur la même classe qui implémente l'interface d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) afin de recevoir une notification d'une opération d'attachement et fournir la possibilité d'annuler l'opération d'attachement.  
  
## Remarques pour les appelants  
 obtenez cette interface en appelant la méthode d' `QueryInterface` dans un objet d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) .  La méthode d' [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) doit être appelée avant que la méthode d' [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) à donner au nœud de programme la possibilité d'arrêter le processus d'attachement.  
  
## méthodes en commande de Vtable  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|-------------|-----------------|  
|[OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)|Se joint au programme associé ou diffère le processus d'attachement à la méthode d' [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .|  
  
## Notes  
 Cette interface est une alternative par défaut à la méthode déconseillée d' [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md) .  Tous les moteurs de débogage sont toujours chargés avec la fonction d' `CoCreateInstance` , c. autrement dit., ils sont instanciés en dehors de l'espace d'adressage du programme débogué.  
  
 Si une implémentation antérieure de la méthode d' `IDebugProgramNode2::Attach_V7` définissait simplement `GUID` du programme débogué, seule la méthode d' [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) doit être implémenté.  
  
 Si une implémentation antérieure de la méthode d' `IDebugProgramNode2::Attach_V7` utilisait l'interface de rappel qui a été fournie, alors que la fonctionnalité doit être déplacée vers une implémentation de la méthode de [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) et de l'interface d' `IDebugProgramNodeAttach2` ne doit pas être implémenté.  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)