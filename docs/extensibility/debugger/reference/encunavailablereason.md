---
description: Représente les raisons pour lesquelles modifier & Continuer n’est pas disponible.
title: EncUnavailableReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1f80dc1454cb1c15feddd099411bcb339dbc58c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151002"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Représente les raisons pour lesquelles **modifier & continuer** n’est pas disponible.

## <a name="syntax"></a>Syntaxe

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
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
Aucune raison spécifique pour laquelle modifier & Continuer n’est pas disponible.

`ENCUN_INTEROP`\
Modifier & Continuer n’est pas disponible pendant un appel InterOp.

`ENCUN_SQLCLR`\
Modifier & Continuer n’est pas disponible pendant un appel de procédure SQL qui utilise le CLR (Common Language Runtime).

`ENCUN_MINIDUMP`\
Modifier & Continuer n’est pas disponible lors du traitement d’un mini-vidage.

`ENCUN_EMBEDDED`\
Modifier & Continuer n’est pas disponible lors du traitement d’un code incorporé.

`ENCUN_ATTACH`\
Modifier & Continuer n’est pas disponible, car la session a été attachée à, et non lancée par le débogueur.

`ENCUN_WIN64`\
Modifier & Continuer n’est pas disponible lors du traitement du code Windows 64 bits.

## <a name="remarks"></a>Notes
Cette énumération est destinée à un usage interne uniquement par [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] . Les méthodes [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) et [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) implémentées par un fournisseur de ports personnalisé doivent toujours retourner `E_NOTIMPL` .

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. idl

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)
