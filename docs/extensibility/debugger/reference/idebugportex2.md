---
title: IDebugPortEx2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5789681b0da70f46dadac1e29d0d6bb9dc905d1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725002"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Cette interface permet au gestionnaire de déboguer de session (SDM) de contrôler les programmes et les processus en cours d’exécution sur un port.

## <a name="syntax"></a>Syntaxe

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface sur le même objet qui implémente [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).

## <a name="notes-for-callers"></a>Notes pour les appelants
 Le SDM appelle [QueryInterface](/cpp/atl/queryinterface) sur l’interface `IDebugPort2` pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugPortEx2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Lance un fichier exécutable.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Reprend l’exécution d’un processus.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Détermine si un processus peut être terminé.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Termine un processus.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Obtient l’ID processus du port lui-même.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Obtient un programme associé à un nœud de programme.|

## <a name="remarks"></a>Notes
 Cette interface est normalement privée entre le SDM et le fournisseur de ports personnalisés.

 Si désiré, un moteur de débogé (DE) peut rechercher cette interface sur [l’interface IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) passé à [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) et utiliser [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) pour lancer le programme. Ce n’est pas une exigence, cependant, et un DE peut faire tout ce qu’il doit faire pour lancer le programme de demande.

## <a name="requirements"></a>Spécifications
 En-tête: portpriv.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
