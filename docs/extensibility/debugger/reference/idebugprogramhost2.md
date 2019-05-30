---
title: IDebugProgramHost2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramHost2
helpviewer_keywords:
- IDebugProgramHost2 interface
ms.assetid: 2c37b3aa-97a9-4665-8709-edd917f18cb1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc7a3222b2fab85657eea1eb0203f8c8da7dd5dc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351215"
---
# <a name="idebugprogramhost2"></a>IDebugProgramHost2
Cette interface fournit des informations sur l’hôte (processus) sur un programme.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramHost2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage implémente cette interface sur le même objet que le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface pour fournir des informations sur le processus d’hébergement. Il s’agit d’une interface facultative.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur un `IDebugProgram2` interface pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugProgramHost2`.

|Méthode|Description|
|------------|-----------------|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostname.md)|Obtient le titre, le nom convivial ou le nom de fichier du processus d’hébergement de ce programme.|
|[GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)|Obtient l’identificateur de processus du processus d’hébergement de ce programme.|
|[GetHostMachineName](../../../extensibility/debugger/reference/idebugprogramhost2-gethostmachinename.md)|Obtient le nom de l’ordinateur que le processus d’hébergement de ce programme est en cours d’exécution.|

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)