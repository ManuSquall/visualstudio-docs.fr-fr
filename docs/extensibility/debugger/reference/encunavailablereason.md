---
title: EncUnavailableReason - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28863549ab3eac96322530bc85c52697f20448c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737169"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`Représente les raisons pour lesquelles **Edit and Continue** n’est pas disponible.

## <a name="syntax"></a>Syntaxe

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
```

## <a name="fields"></a>Champs
`ENCUN_NONE`\
Aucune raison précise pour laquelle Edit and Continue n’est pas disponible.

`ENCUN_INTEROP`\
Edit and Continue n’est pas disponible lors d’un appel InterOp.

`ENCUN_SQLCLR`\
Edit and Continue n’est pas disponible lors d’un appel de procédure SQL qui utilise le common Language Runtime (CLR).

`ENCUN_MINIDUMP`\
Edit and Continue n’est pas disponible lors du traitement d’un mini-dump.

`ENCUN_EMBEDDED`\
Edit and Continue n’est pas disponible lors du traitement du code intégré.

`ENCUN_ATTACH`\
Edit and Continue n’est pas disponible parce que la session a été jointe à, pas lancé par, le débbugger.

`ENCUN_WIN64`\
Edit and Continue n’est pas disponible lors du traitement du code Windows 64 bits.

## <a name="remarks"></a>Notes
Cette énumération est pour un [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]usage interne seulement par . Les méthodes [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) et [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) mises en œuvre par un fournisseur de ports personnalisés doivent toujours revenir. `E_NOTIMPL`

## <a name="requirements"></a>Spécifications
En-tête: msdbg.idl

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
