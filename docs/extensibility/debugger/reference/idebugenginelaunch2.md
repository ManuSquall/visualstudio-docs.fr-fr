---
title: IDebugEngineLaunch2 - France Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730496"
---
# <a name="idebugenginelaunch2"></a>IDebugEngineLaunch2
Utilisé par un moteur de débogé (DE) pour lancer et mettre fin aux programmes.

## <a name="syntax"></a>Syntaxe

```
IDebugEngineLaunch2 : IDebugEngine2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Cette interface est implémentée par un DE personnalisé si elle a des exigences spéciales pour le lancement d’un processus qui ne peut pas être géré entièrement par un port personnalisé. C’est généralement le cas lorsque le DE fait partie d’un interprète et le processus en cours de débogé est un script: l’interprète doit être lancé d’abord, puis le script est chargé et commencé. Un port peut lancer l’interprète, mais le script peut nécessiter une manipulation spéciale (c’est là que le DE a un rôle). Cette interface n’est implémentée que s’il existe des exigences uniques pour le lancement d’un programme qu’un port personnalisé ne peut pas gérer.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est appelée par le gestionnaire de déboçon de session (SDM) si le SDM peut obtenir cette interface à partir de [l’interface IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) (en utilisant QueryInterface). Si cette interface peut être obtenue, le SDM sait que le DE a des exigences spéciales et appelle cette interface pour lancer le programme au lieu d’avoir le port de le lancer.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugEngineLaunch2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)|Lance un processus au moyen de la DE.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)|Reprend l’exécution du processus.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-canterminateprocess.md)|Détermine si un processus peut être terminé.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)|Termine un processus.|

## <a name="requirements"></a>Spécifications
 En-tête: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
