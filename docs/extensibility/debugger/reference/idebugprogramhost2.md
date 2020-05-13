---
title: IDebugProgramHost2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64db456e0c438f8665f122c3cd1b079c2ad1cea1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722212"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
Cette interface fournit des informations d’hôte (processus) sur un programme.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé implémente cette interface sur le même objet que l’interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) pour fournir des informations sur le processus d’hébergement. Il s’agit d’une interface facultative.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [QueryInterface](/cpp/atl/queryinterface) `IDebugProgram2` sur une interface pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugProgramHost2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Obtient le titre, le nom amical, ou le nom de fichier du processus d’hébergement de ce programme.|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Obtient l’identifiant de processus du processus d’hébergement de ce programme.|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Obtient le nom de la machine le processus d’hébergement de ce programme est en cours d’exécution sur.|

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
