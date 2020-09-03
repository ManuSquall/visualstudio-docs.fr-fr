---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1633c5e9aa6ff251fedce83a0243664cd9e0e0a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737915"
---
# <a name="bp_passcount_style"></a>BP_PASSCOUNT_STYLE
Spécifie la condition associée au nombre de passes de point d’arrêt qui provoque le déclenchement du point d’arrêt.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
typedef DWORD BP_PASSCOUNT_STYLE;
```

```csharp
public enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
```

## <a name="fields"></a>Champs
`BP_PASSCOUNT_NONE`\
Ne spécifie aucun style de nombre de tests de point d’arrêt.

`BP_PASSCOUNT_EQUAL`\
Définit le style de nombre de passes de point d’arrêt sur égal. Le point d’arrêt est déclenché lorsque le nombre de fois où le point d’arrêt est atteint est égal au nombre de passes.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
Définit le style de nombre de passes de point d’arrêt sur égal ou supérieur. Le point d’arrêt est déclenché lorsque le nombre de fois où le point d’arrêt est atteint est supérieur ou égal au nombre de passes.

`BP_PASSCOUNT_MOD`\
Spécifie un nombre de passes modulo. Par exemple, si le nombre de tests est de type `BP_PASSCOUNT_MOD` et que la valeur du nombre de passes est 4, le point d’arrêt est déclenché chaque fois que le nombre d’accès est un multiple de 4.

## <a name="remarks"></a>Notes
Utilisé pour le `stylePassCount` membre de la structure [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) qui est à son tour membre des structures [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
