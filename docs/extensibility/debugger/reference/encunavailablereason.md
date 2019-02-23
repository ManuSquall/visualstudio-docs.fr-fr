---
title: EncUnavailableReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea1bbf8fe96abbf1e7bd9a92396d0dcfa4306445
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717037"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Représente les raisons qui **Modifier & Continuer** n’est pas disponible.

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

#### <a name="parameters"></a>Paramètres
ENCUN_NONE non absolument pourquoi Modifier & Continuer n’est pas disponible.

ENCUN_INTEROP Modifier & Continuer n’est pas disponible pendant un appel InterOp.

ENCUN_SQLCLR Modifier & Continuer n’est pas disponible pendant un appel de procédure SQL qui utilise le Common Language Runtime (CLR).

ENCUN_MINIDUMP Modifier & Continuer n’est pas disponible lors du traitement d’un minidump.

ENCUN_EMBEDDED Modifier & Continuer n’est pas disponible lors du traitement du code incorporé.

ENCUN_ATTACH Modifier & Continuer n’est pas disponible, car la session a été attachée à, pas lancé par le débogueur.

ENCUN_WIN64 Modifier & Continuer n’est pas disponible lors du traitement du code de Windows 64 bits.

## <a name="remarks"></a>Notes
Cette énumération est par rapport à un usage interne uniquement par [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]. Le [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) et [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) méthodes implémenté par un fournisseur de port personnalisé doivent toujours retourner `E_NOTIMPL`.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.idl

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
