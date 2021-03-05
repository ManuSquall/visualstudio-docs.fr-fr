---
description: Cette interface permet au gestionnaire de débogage de session (SDM) de contrôler les programmes et les processus en cours d’exécution sur un port.
title: IDebugPortEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 54da202e6bbaf08216b921afbde2e39f1da3a788
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142789"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Cette interface permet au gestionnaire de débogage de session (SDM) de contrôler les programmes et les processus en cours d’exécution sur un port.

## <a name="syntax"></a>Syntaxe

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface sur le même objet qui implémente [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le SDM appelle [QueryInterface](/cpp/atl/queryinterface) sur l' `IDebugPort2` interface pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugPortEx2` .

|Méthode|Description|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Lance un fichier exécutable.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Reprend l’exécution d’un processus.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Détermine si un processus peut être arrêté.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Termine un processus.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Obtient l’ID de processus du port lui-même.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Obtient un programme associé à un nœud de programme.|

## <a name="remarks"></a>Notes
 Cette interface est normalement privée entre le SDM et le fournisseur de ports personnalisés.

 Si vous le souhaitez, un moteur de débogage (DE) peut rechercher cette interface sur l’interface [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) transmise à [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) et utiliser [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) pour lancer le programme. Toutefois, ce n’est pas obligatoire et un DE peut faire tout ce qu’il doit faire pour lancer le programme de demande.

## <a name="requirements"></a>Configuration requise
 En-tête : portpriv. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
