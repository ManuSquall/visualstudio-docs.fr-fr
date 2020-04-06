---
title: IDebugProviderProgramNode2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 815a945f6fb591960ebf0bf4b4fcd9d842ffefd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720681"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Cette interface mobilise des interfaces liées au programme au-delà des limites du processus.

## <a name="syntax"></a>Syntaxe

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface sur le même objet qui implémente [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) pour prendre en charge les interfaces de marshaling au-delà des frontières du processus.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [QueryInterface](/cpp/atl/queryinterface) `IDebugProgramNode2` sur une interface pour obtenir cette interface. Si cette interface ne peut pas être obtenue, le DE ne prend pas en charge le marshaling des interfaces.

## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable
 Cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Obtient une interface spécifiée au-delà des limites du processus.|

## <a name="remarks"></a>Notes
 Cette interface est implémentée lorsque le DE s’exécute dans un espace de processus distinct du programme en cours de déboguer: par exemple, lorsque le DE est en cours d’exécution dans l’espace de processus Visual Studio au lieu de l’espace de processus du programme étant débogé.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
