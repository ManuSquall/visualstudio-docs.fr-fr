---
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ded3d31f9be2d0a02a238ead4bc989cc21b4922a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351823"
---
# <a name="bpcondstyle"></a>BP_COND_STYLE
Spécifie le style de condition de point d’arrêt pour en attente et de points d’arrêt liés.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
typedef DWORD BP_COND_STYLE;
```

```csharp
public enum enum_BP_COND_STYLE {
    BP_COND_NONE         = 0x0000,
    BP_COND_WHEN_TRUE    = 0x0001,
    BP_COND_WHEN_CHANGED = 0x0002
};
```

## <a name="fields"></a>Champs
`BP_COND_NONE`\
Se déclenche le point d’arrêt lors de la position du point d’arrêt est atteint. Aucune condition de point d’arrêt spécifiée.

`BP_COND_WHEN_TRUE`\
Se déclenche le point d’arrêt uniquement lorsque l’expression conditionnelle associé au point d’arrêt a la valeur `true`.

`BP_COND_WHEN_CHANGED`\
Se déclenche le point d’arrêt uniquement lorsque le point d’arrêt associé à la valeur de l’expression conditionnelle a changé dans son évaluation précédente.

## <a name="remarks"></a>Notes
Utilisé pour le `styleCondition` membre de la [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) structure.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
