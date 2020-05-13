---
title: IDebugProgramNode2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2
helpviewer_keywords:
- IDebugProgramNode2 interface
ms.assetid: 80e511d8-9b40-4a85-aa5d-952fa5ee6ae7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e6eac7c97b9d375f32e36a372d6f31175c79098
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721919"
---
# <a name="idebugprogramnode2"></a>IDebugProgramNode2
Cette interface représente un programme qui peut être déboqué.

## <a name="syntax"></a>Syntaxe

```
IDebugProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un moteur de débogé (DE) ou un fournisseur de port personnalisé implémente cette interface pour représenter un programme qui peut être déboqué. Cette interface est généralement implémentée sur le même objet qui implémente l’interface [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md) Cette interface est [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] enregistrée avec en appelant [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) pour retourner cette interface. Un fournisseur de port personnalisé reçoit cette interface par le biais d’un appel à [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). A DE reçoit cette interface par le biais d’un appel à [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md).

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugProgramNode2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetProgramName](../../../extensibility/debugger/reference/idebugprogramnode2-getprogramname.md)|Obtient le nom d’un programme.|
|[GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)|Obtient le nom du processus d’hébergement d’un programme.|
|[GetHostPid](../../../extensibility/debugger/reference/idebugprogramnode2-gethostpid.md)|Obtient l’identifiant de processus système pour le processus d’hébergement d’un programme.|
|[GetHostMachineName_V7](../../../extensibility/debugger/reference/idebugprogramnode2-gethostmachinename-v7.md)|Déconseillée. NE PAS UTILISER.|
|[Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)|Déconseillée. NE PAS UTILISER. Voir l’interface [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) pour une approche alternative.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)|Obtient le nom et l’identifiant de l’EXÉCUTER DE ce programme.|
|[DetachDebugger_V7](../../../extensibility/debugger/reference/idebugprogramnode2-detachdebugger-v7.md)|Déconseillée. NE PAS UTILISER.|

## <a name="remarks"></a>Notes
 Le gestionnaire de déboque de session (SDM) appelle généralement [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md) pour obtenir cette interface.

## <a name="requirements"></a>Spécifications
 En-tête: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)
- [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)
