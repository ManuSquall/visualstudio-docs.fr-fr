---
title: DISASSEMBLY_STREAM_SCOPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 446b0eec7593457ed2cd384eb9a6bca383094e62
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684492"
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

## <a name="members"></a>Membres
DSS_HUGE spécifie qui désassembler le contexte de code génèrent une sortie plus qu’un client veut généralement récupérer dans un seul appel.

DSS_FUNCTION Spécifie que la fonction contenue dans le contexte de code doit être démonté. Spécifie que le flux de code machine représente une fonction, lorsque retournée par la [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) (méthode).

DSS_MODULE lorsque retourné par la `IDebugDisassemblyStream2::GetScope` méthode, spécifie que le flux de code machine représente un module.

DSS_ALL Spécifie le code machine pour l’espace d’adressage entière.

## <a name="remarks"></a>Notes
Passé en tant qu’argument à la [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) méthode et retourné par le [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) (méthode).

Ces valeurs peuvent être combinées avec un opérateur de bits `OR`.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
