---
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8ca4f551f4dd6541bad9d73b5e91c671ad80492
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318301"
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

## <a name="members"></a>Membres
BP_COND_NONE  
Se déclenche le point d’arrêt lors de la position du point d’arrêt est atteint. Aucune condition de point d’arrêt spécifiée.

BP_COND_WHEN_TRUE  
Se déclenche le point d’arrêt uniquement lorsque l’expression conditionnelle associé au point d’arrêt a la valeur `true`.

BP_COND_WHEN_CHANGED  
Se déclenche le point d’arrêt uniquement lorsque le point d’arrêt associé à la valeur de l’expression conditionnelle a changé dans son évaluation précédente.

## <a name="remarks"></a>Notes
Utilisé pour le `styleCondition` membre de la [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) structure.

## <a name="requirements"></a>Spécifications
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
[Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
