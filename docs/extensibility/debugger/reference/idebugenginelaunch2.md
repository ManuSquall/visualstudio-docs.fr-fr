---
title: IDebugEngineLaunch2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1abff9f393b34bbf5950c9e56b6f489f332840db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Utilisé par un moteur de débogage (DE) pour démarrer et arrêter les programmes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Cette interface est implémentée par un personnalisées DE s’il a des exigences spéciales pour le lancement d’un processus qui ne peut pas être géré entièrement par un port personnalisé. Cela est généralement le cas lorsque le DE fait partie d’un interpréteur et le processus en cours de débogage est un script : l’interpréteur doit être démarré en premier, puis le script est chargé et démarré. Un port peut lancer l’interpréteur, mais le script peut nécessiter un traitement spécial (c'est-à-dire où le D’a un rôle). Cette interface est implémentée uniquement s’il existe des exigences uniques de lancement d’un programme qui a un port personnalisé ne peut pas traiter.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est appelée par le Gestionnaire de session de débogage (SDM) si le SDM peut accéder à cette interface à partir de la [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (à l’aide de QueryInterface) de l’interface. Si cette interface peut être obtenue, le SDM sait que le DE a des exigences particulières et appelle cette interface pour lancer le programme au lieu d’avoir le port à lancer.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugEngineLaunch2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Lance un processus au moyen de la DE.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Reprend l’exécution de processus.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Détermine si un processus peut être arrêté.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Arrête un processus.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)