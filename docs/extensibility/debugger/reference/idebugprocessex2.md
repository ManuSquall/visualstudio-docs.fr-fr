---
title: IDebugProcessEx2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 743dd1aa72d9b8db6b848618c8a2ad6c8c8ecaaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723329"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Cette interface permet au gestionnaire de débogé de session (SDM) d’aviser un processus qu’il s’attache au processus ou se détache.

## <a name="syntax"></a>Syntaxe

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface sur le même objet que l’interface [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) afin de :

- Suivi de support des sessions liées à un processus

- Support auto-attacher sur plusieurs moteurs de débogé

  Le fournisseur de ports personnalisé peut implémenter cette interface s’il le souhaite.

## <a name="notes-for-callers"></a>Notes pour les appelants

- Le SDM appelle [QueryInterface](/cpp/atl/queryinterface) sur une `IDebugProcess2` interface pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugProcessEx2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Attach](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informe le processus qu’une session est en train de déboguer le processus.|
|[Detach](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informe le processus qu’une session n’est plus en train de déboguer le processus.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Ajoute des nœuds de programme pour une liste de moteurs débogés.|

## <a name="remarks"></a>Notes
 Cette interface est privée entre le SDM et le processus.

## <a name="requirements"></a>Spécifications
 En-tête: Portpriv.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
