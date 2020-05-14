---
title: EXCEPTION_INFO Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EXCEPTION_INFO
helpviewer_keywords:
- EXCEPTION_INFO structure
ms.assetid: d046957a-b97d-420b-b46b-c67cbaef709e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a305d34123d02b1fdbd545a438db4461643ed185
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737020"
---
# <a name="exception_info"></a>EXCEPTION_INFO
Décrit une erreur d’exception ou de temps d’exécution lancée par le programme étant débogé.

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
`pProgram`\
[L’objet IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme dans lequel l’exception s’est produite.

`bstrProgramName`\
Le nom du programme dans lequel l’exception s’est produite.

`bstrExceptionName`\
Nom de l'exception.

`dwCode`\
Le code d’identification pour l’erreur d’exception ou de temps d’exécution.

`dwState`\
Une valeur de [l’énumération EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md) qui définit l’état de l’exception.

`guidType`\
L’identifiant de langue `guidLang` `guidEng`GUID, soit ou .

## <a name="remarks"></a>Notes
Cette structure est transmise comme paramètre aux méthodes [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) et [RemoveSetException.](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) Cette structure est également transmise à la méthode [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) à remplir.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EXCEPTION_STATE](../../../extensibility/debugger/reference/exception-state.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)
- [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)
- [GetException](../../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md)
