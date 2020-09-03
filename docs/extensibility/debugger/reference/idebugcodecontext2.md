---
title: IDebugCodeContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 778602cc29049d855c418fd8fa416feb1ad8e9fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734213"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Cette interface représente la position de départ d’une instruction de code. Pour la plupart des architectures Runtime actuelles, un contexte de code peut être considéré comme une adresse dans le flux d’exécution d’un programme.

## <a name="syntax"></a>Syntaxe

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogage implémente cette interface pour relier la position d’une instruction de code à la position d’un document.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Les méthodes de nombreuses interfaces retournent cette interface, généralement [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Il est également utilisé de manière intensive avec l’interface [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) et les informations de résolution des points d’arrêt.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Outre les méthodes sur l’interface [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Obtient le contexte de document qui correspond au contexte de code actif.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Obtient les informations de langage pour ce contexte de code.|

## <a name="remarks"></a>Notes
 La principale différence entre une `IDebugCodeContext2` interface et une interface [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) est qu’un `IDebugCodeContext2` est toujours aligné sur les instructions. Cela signifie qu’un `IDebugCodeContext2` est toujours en pointant vers le début d’une instruction, tandis qu’un `IDebugMemoryContext2` peut pointer vers n’importe quel octet de mémoire dans l’architecture Runtime. `IDebugCodeContext2` est incrémenté par des instructions plutôt que par la taille de stockage de base (généralement Byte).

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Next](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
