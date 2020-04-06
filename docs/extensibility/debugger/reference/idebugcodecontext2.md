---
title: IDebugCodeContext2 - France Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734213"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Cette interface représente la position de départ d’une instruction de code. Pour la plupart des architectures de temps de ruissellement aujourd’hui, un contexte de code peut être considéré comme une adresse dans le flux d’exécution d’un programme.

## <a name="syntax"></a>Syntaxe

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé implémente cette interface pour relier la position d’une instruction de code à une position de document.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Méthodes sur de nombreuses interfaces retourner cette interface, le plus généralement, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Il est également largement utilisé avec [l’interface IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) ainsi que dans les informations de résolution de point de rupture.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes de l’interface [IDebugMemoryContext2,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) cette interface met en œuvre les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Obtient le contexte de document qui correspond au contexte actif du code.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Obtient les informations linguistiques pour ce contexte de code.|

## <a name="remarks"></a>Notes
 La principale différence `IDebugCodeContext2` entre une interface et une interface [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) est qu’une interface est toujours alignée sur l’instruction. `IDebugCodeContext2` Cela signifie `IDebugCodeContext2` qu’un est toujours pointant vers `IDebugMemoryContext2` le début d’une instruction, alors qu’un peut pointer vers n’importe quel byte de mémoire dans l’architecture de run-time. `IDebugCodeContext2`est incrémenté par des instructions plutôt que par la taille de stockage de base (généralement byte).

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Suivant](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
