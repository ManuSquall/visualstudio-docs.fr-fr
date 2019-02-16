---
title: COMPUTER_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- COMPUTER_INFO structure
ms.assetid: 943085b2-f165-462d-9a4e-2086f0cdfff4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 183c079206dd4c16a9301e370abec2f9351b1f61
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316832"
---
# <a name="computerinfo"></a>COMPUTER_INFO
Décrit l’ordinateur sur lequel le débogueur est en cours d’exécution.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagCOMPUTER_INFO
{
    WORD wProcessorArchitecture;
    WORD wSuiteMask;
    DWORD dwOperatingSystemVersion;
} COMPUTER_INFO;
```

```csharp
public struct COMPUTER_INFO
{
    public ushort wProcessorArchitecture;
    public ushort wSuiteMask;
    public uint dwOperatingSystemVersion;
}
```

## <a name="terms"></a>Termes
wProcessorArchitecture  
Identifie l’architecture du microprocesseur.

wSuiteMask  
Identifie le masque de suite.

dwOperatingSystemVersion  
Numéro de version de système d’exploitation.

## <a name="remarks"></a>Notes
Cette structure est retournée par la [GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md) (méthode).

## <a name="requirements"></a>Spécifications
En-tête : Msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
[Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)  
[GetComputerInfo](../../../extensibility/debugger/reference/idebugwindowscomputerport2-getcomputerinfo.md)
