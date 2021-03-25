---
description: Cette interface représente un programme pouvant être débogué.
title: IDebugProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 55bd6180c3b7681196e72460c951ffeafe9f2cf7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087273"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Cette interface représente un programme pouvant être débogué.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un moteur DE débogage (DE) ou un fournisseur de port personnalisé implémente cette interface pour représenter un programme pouvant être débogué. Cette interface est généralement implémentée sur le même objet qui implémente l’interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) . Cette interface est inscrite auprès de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] en appelant [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) pour retourner cette interface. Un fournisseur de port personnalisé reçoit cette interface via un appel à [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Un DE reçoit cette interface via un appel à [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugProgramNode2` .

|Méthode|Description|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Obtient le nom d’un programme.|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Obtient le nom du processus hébergeant un programme.|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Obtient l’identificateur de processus système pour le processus qui héberge un programme.|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|Déconseillé. N’UTILISEZ PAS.|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|Déconseillé. N’UTILISEZ PAS. Pour une autre approche, consultez l’interface [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) .|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Obtient le nom et l’identificateur du en cours d’exécution de ce programme.|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|Déconseillé. N’UTILISEZ PAS.|

## <a name="remarks"></a>Notes
 Le gestionnaire de débogage de session (SDM) appelle généralement [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) pour obtenir cette interface.

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
