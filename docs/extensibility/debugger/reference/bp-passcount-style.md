---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 809c63fe536166efe0779cd4e4dc0149b219390a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686052"
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
Spécifie la condition associée au nombre de passage de point d’arrêt qui provoque le point d’arrêt à déclencher.

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

## <a name="members"></a>Membres
BP_PASSCOUNT_NONE ne spécifie aucun style de nombre de pass de point d’arrêt.

BP_PASSCOUNT_EQUAL définit le style de nombre de passage de point d’arrêt à égal. Le point d’arrêt se déclenche lorsque le nombre de fois où que le point d’arrêt est atteint égale au nombre de pass.

BP_PASSCOUNT_EQUAL_OR_GREATER définit le style de nombre de passage de point d’arrêt sur égale ou supérieure. Le point d’arrêt se déclenche lorsque le nombre de fois où que le point d’arrêt est atteint est égal à ou supérieur au nombre de pass.

BP_PASSCOUNT_MOD spécifie un modulo passer le nombre. Par exemple, si le nombre de pass est du type `BP_PASSCOUNT_MOD` et la valeur du nombre pass est 4, le se de point d’arrêt déclenche chaque fois que le nombre d’accès est un multiple de 4.

## <a name="remarks"></a>Notes
Utilisé pour le `stylePassCount` membre de la [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) structure qui est à son tour un membre de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) et [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) structures.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
