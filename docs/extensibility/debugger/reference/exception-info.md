---
title: EXCEPTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c5863c9ebb790ebcbc267f62cc2a0a1fd14603c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686260"
---
# <a name="exceptioninfo"></a>EXCEPTION_INFO
Décrit une exception ou une erreur d’exécution levées par le programme en cours de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagEXCEPTION_INFO {
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    BSTR            bstrExceptionName;
    DWORD           dwCode;
    EXCEPTION_STATE dwState;
    GUID            guidType;
} EXCEPTION_INFO;
```

```csharp
public struct EXCEPTION_INFO {
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public string         bstrExceptionName;
    public uint           dwCode;
    public uint           dwState;
    public Guid           guidType;
};
```

## <a name="members"></a>Membres
pProgram le [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objet qui représente le programme dans lequel l’exception s’est produite.

bstrProgramName le nom du programme dans lequel l’exception s’est produite.

bstrExceptionName le nom de l’exception.

dwCode le code d’identification de l’erreur d’exception ou d’exécution.

valeur dwState A à partir de la [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) énumération qui définit l’état de l’exception.

identificateur de langue de GUID guidType, soit `guidLang` ou `guidEng`.

## <a name="remarks"></a>Notes
Cette structure est passée en tant que paramètre à la [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) et [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) méthodes. Cette structure est également passée à la [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) méthode doit être renseigné.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
