---
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59573736ca3cd0768d3383e5621d96dffdea9746
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338900"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Cette interface représente la position de départ d’une instruction de code. Pour la plupart des architectures d’exécution dès aujourd'hui, un contexte de code peut être considéré comme une adresse dans le flux de l’exécution d’un programme.

## <a name="syntax"></a>Syntaxe

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage implémente cette interface pour associer la position d’une instruction de code vers une position de document.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Les méthodes sur le nombre d’interfaces retournent cette interface, plus généralement, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Il est également largement utilisé avec le [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) interface ainsi que dans les informations de résolution de point d’arrêt.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Outre les méthodes sur le [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interface, cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Obtient le contexte de document correspondant au contexte de code actif.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Obtient les informations de langue pour ce contexte de code.|

## <a name="remarks"></a>Notes
 La principale différence entre un `IDebugCodeContext2` interface et un [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interface est qu’un `IDebugCodeContext2` est toujours instruction aligné. Cela signifie qu’un `IDebugCodeContext2` pointe toujours vers le début d’une instruction, tandis qu’un `IDebugMemoryContext2` peut pointer vers n’importe quel octet de mémoire dans l’architecture de l’exécution. `IDebugCodeContext2` est incrémenté par instructions plutôt que par la taille de stockage de base (généralement octets).

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Next](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)