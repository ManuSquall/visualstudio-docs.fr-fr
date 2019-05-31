---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 724e32f83cfec31c2bacdab661407983af87efe6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318240"
---
# <a name="disassemblystreamscope"></a>DISASSEMBLY_STREAM_SCOPE
Spécifie l’étendue du flux de code machine.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="fields"></a>Champs
`DSS_HUGE`\
Spécifie que le contexte de code de désassemblage générerait une sortie plus qu’un client veut généralement récupérer dans un seul appel.

`DSS_FUNCTION`\
Spécifie que la fonction contenue dans le contexte de code doit être démontée. Spécifie que le flux de code machine représente une fonction, lorsque retournée par la [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) (méthode).

`DSS_MODULE`\
Quand retournée par la `IDebugDisassemblyStream2::GetScope` méthode, spécifie que le flux de code machine représente un module.

`DSS_ALL`\
Spécifie le code machine pour l’espace d’adressage entière.

## <a name="remarks"></a>Notes
Passé en tant qu’argument à la [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) méthode et retourné par le [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) (méthode).

Ces valeurs peuvent être combinées avec un opérateur de bits `OR`.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
