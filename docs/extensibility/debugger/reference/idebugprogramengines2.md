---
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1a5ad34904a2f0bf02e5a2221f1ff73093012a41
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916928"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Cette interface est utilisée par les nœuds de programme pour spécifier tous les moteurs de débogage possible (dé) qui peuvent déboguer ce programme.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Un dé ou un fournisseur de port personnalisé implémente cette interface sur le même objet qui implémente [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) pour prendre en charge l’établissement d’un DE spécifique à utiliser pour un programme particulier.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur un `IDebugProgramNode2` interface pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugProgramEngines2`.

|Méthode|Description|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Indique tous les possibles DEs que pouvez déboguer ce programme.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Sélectionne le DE à utiliser pour déboguer ce programme.|

## <a name="remarks"></a>Notes
 Une fois qu’un D’est choisi par l’utilisateur, ce choix est inscrit avec le nœud de programme en appelant [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md). Le moteur sélectionné devient le moteur retourné par [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md).

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)