---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ccbe76d800be035bc39caa477955b91bf21c074e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195675"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Utilisé par un moteur de débogage (dé) pour lancer et arrêter des programmes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugEngineLaunch2 : IDebugEngine2  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Cette interface est implémentée par un DE personnalisé s’il a des exigences particulières pour le lancement d’un processus qui ne peut pas être géré entièrement par un port personnalisé. C’est généralement le cas lorsque le DE fait partie d’un interpréteur et que le processus en cours de débogage est un script : l’interpréteur doit être lancé tout d’abord, puis le script est chargé et démarré. Un port peut lancer l’interpréteur, mais le script peut nécessiter un traitement spécial (c'est-à-dire où le dé a un rôle). Cette interface est implémentée uniquement s’il existe des exigences uniques pour le lancement d’un programme qui a un port personnalisé ne peut pas gérer.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Cette interface est appelée par le Gestionnaire de session de débogage (SDM) si le SDM peut obtenir cette interface à partir de la [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (à l’aide de QueryInterface) de l’interface. Si cette interface peut être obtenue, le SDM sait que le dé a des exigences particulières et appelle cette interface pour lancer le programme au lieu d’avoir le port lancez-le.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugEngineLaunch2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Lance un processus au moyen de l’Allemagne.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Reprend l’exécution du processus.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Détermine si un processus peut être arrêté.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Arrête un processus.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
