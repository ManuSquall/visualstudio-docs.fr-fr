---
title: "IDebugEngine2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2"
helpviewer_keywords: 
  - "Interface de IDebugEngine2"
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette interface représente un moteur de débogage \(DE\).  Il est utilisé pour gérer différents aspects d'une session de débogage, de créer des points d'arrêt à définir et à désactiver des exceptions.  
  
## Syntaxe  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## Remarques à l'intention des implémenteurs  
 Cette interface est implémentée par un personnalisé De pour gérer le débogage des programmes.  cette interface doit être implémentée par le De.  
  
## Remarques pour les appelants  
 Cette interface est appelée par le gestionnaire de débogage de session \(SDM\) pour gérer la session de débogage, y compris la gestion des exceptions, créer des points d'arrêt, et la réponse aux événements synchrones envoyés par le De.  
  
## méthodes en commande de Vtable  
 Le tableau suivant répertorie les méthodes d' `IDebugEngine2`.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|crée un énumérateur pour tous les programmes débogué par un De.|  
|[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)|joint un De à un programme.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Crée un point d'arrêt en attente du.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Spécifie comment le De doit gérer une exception donnée.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Supprime l'exception spécifié elle n'est plus gérée par le moteur de débogage.|  
|[RemoveAllSetExceptions](../Topic/IDebugEngine2::RemoveAllSetExceptions.md)|Supprime la liste d'exceptions que l'IDE a définies pour une architecture ou d'un langage à l'exécution particulière.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Obtient le GUID du De.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Signale à que le programme spécifié a été atypiquement terminé et que le De doit nettoyer toutes les références au programme et envoyer un programme destroy l'événement.|  
|[ContinueFromSynchronousEvent](../Topic/IDebugEngine2::ContinueFromSynchronousEvent.md)|Appelé par le SDM pour indiquer qu'un événement synchrone de débogage, précédemment envoyés par le De au SDM, était accepté et traité.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|définit les paramètres régionaux du De.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Définit la racine de Registre actuellement utilisé par le De.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|définit un métrique.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Les demandes que tous les programmes débogué par ce De arrêtent l'exécution la prochaine fois un de leurs thread essaie de s'exécuter.|  
  
## Configuration requise  
 en\-tête : Msdbg.h  
  
 l'espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Voir aussi  
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)