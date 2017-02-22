---
title: "IDebugModule2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2"
helpviewer_keywords: 
  - "Interface de IDebugModule2"
ms.assetid: 24c2a126-f4ab-4891-8509-8ef99b994c08
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugModule2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette interface représente module\-qu'est, une unité exécutable d'un programme\-tel en tant que DLL.  
  
## Syntaxe  
  
```  
IDebugModule2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Le moteur \(DE\) de débogage implémente cette interface pour représenter un module et fournir l'accès aux informations relatives à ce module.  
  
## Remarques pour les appelants  
 Un appel à [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md) retourne cette interface.  Le De envoie l'interface d' [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) au gestionnaire de débogage de session \(SDM\) à l'aide de la méthode d' [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) .  
  
 cette interface peut également être retournée dans une structure de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) \(qui est retournée par un appel à [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)\).  
  
 [Suivant](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) retourne également cette interface \(retour d'[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) l'interface d' [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md) \).  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugModule2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)|obtient [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) qui décrit ce module.|  
|[ReloadSymbols\_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md)|OBSOLÈTE.  NE SUR UTILISEZ NOT.  recharge les symboles pour ce module.|  
  
## Notes  
 Les informations de module peuvent être affichées dans la fenêtre de **Module** de l'IDE.  
  
## Configuration requise  
 en\-tête : msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetModule](../../../extensibility/debugger/reference/idebugmoduleloadevent2-getmodule.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)   
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)