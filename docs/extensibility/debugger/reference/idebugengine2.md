---
title: IDebugEngine2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 95a1a8c48bd6eab0f21ccc85a125b5d10f42ef4e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugengine2"></a>IDebugEngine2
Cette interface représente un moteur de débogage (DE). Il est utilisé pour gérer différents aspects d’une session de débogage à partir de la création de points d’arrêt pour sélectionner et désélectionner des exceptions.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Cette interface est implémentée par un DE personnalisée pour gérer le débogage des programmes. Cette interface doit être implémentée par le DE.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est appelée par le Gestionnaire de session de débogage (SDM) pour gérer la session de débogage, y compris la gestion des exceptions, création de points d’arrêt et la réponse à des événements synchrones envoyés par le DE.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugEngine2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Crée un énumérateur pour tous les programmes en cours de débogage par un DE.|  
|[Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Attache un DE à un programme.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Crée un point d’arrêt en attente dans le DE.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Spécifie la façon dont le DE doit gérer une exception donnée.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Supprime l’exception spécifiée afin qu’il n’est n’est plus géré par le moteur de débogage.|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Supprime la liste des exceptions, que l’IDE a définie pour un langage ou une architecture d’exécution particulière.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Obtient le GUID de la DE.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informe un DE que le programme spécifié a été arrêté anormalement et que le doit nettoyer toutes les références au programme et envoyer un programme détruire l’événement.|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Appelé par le SDM pour indiquer qu’un événement de débogage synchrone précédemment envoyé par le DE pour le SDM, a été reçu et traité.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Définit les paramètres régionaux de la DE.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Définit la racine de Registre actuellement en cours d’utilisation par le DE.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Définit une mesure.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Demande que tous les programmes en cours de débogage par cette DE s’arrêter l’exécution de la prochaine fois qu’un de leurs threads tente de s’exécuter.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)