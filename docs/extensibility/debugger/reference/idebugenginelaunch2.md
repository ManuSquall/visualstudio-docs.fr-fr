---
title: IDebugEngineLaunch2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2
helpviewer_keywords:
- IDebugEngineLaunch2 interface
ms.assetid: 5eaf2ad8-3fbf-446e-b48b-5327ad3f5255
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee77cbd680df2c851d53aac298605023227fa6f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730496"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Utilisé par un moteur de débogage (DE) pour lancer et terminer des programmes.

## <a name="syntax"></a>Syntaxe

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par un personnalisé DE si elle a des exigences spéciales pour le lancement d’un processus qui ne peut pas être entièrement géré par un port personnalisé. C’est généralement le cas lorsque la méthode DE fait partie d’un interpréteur et que le processus en cours de débogage est un script : l’interpréteur doit d’abord être lancé, puis le script est chargé et démarré. Un port peut lancer l’interpréteur, mais le script peut nécessiter un traitement spécial (c’est là que le DE a un rôle). Cette interface est implémentée uniquement s’il existe des exigences uniques pour lancer un programme qu’un port personnalisé ne peut pas gérer.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est appelée par le gestionnaire de débogage de session (SDM) si le SDM peut récupérer cette interface à partir de l’interface [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (à l’aide de QueryInterface). Si cette interface peut être obtenue, le SDM sait que le DE a des exigences spéciales et appelle cette interface pour lancer le programme au lieu de l’exécuter par le port.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugEngineLaunch2` .

|Méthode|Description|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Lance un processus à l’aide de la méthode de.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Reprend l’exécution du processus.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Détermine si un processus peut être arrêté.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Termine un processus.|

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
