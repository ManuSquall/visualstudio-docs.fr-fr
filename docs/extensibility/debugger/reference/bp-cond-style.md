---
description: Spécifie le style de condition de point d’arrêt pour les points d’arrêt en attente et liés.
title: BP_COND_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 611df036ff876e10096013070cac097bc51a8986
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105085414"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Spécifie le style de condition de point d’arrêt pour les points d’arrêt en attente et liés.

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
Déclenche le point d’arrêt lorsque la position du point d’arrêt est atteinte. Aucune condition de point d’arrêt spécifiée.

`BP_COND_WHEN_TRUE`\
Déclenche le point d’arrêt uniquement lorsque l’expression conditionnelle associée au point d’arrêt a la valeur `true` .

`BP_COND_WHEN_CHANGED`\
Déclenche le point d’arrêt uniquement lorsque la valeur de l’expression conditionnelle associée au point d’arrêt a été modifiée par rapport à son évaluation précédente.

## <a name="remarks"></a>Notes
Utilisé pour le `styleCondition` membre de la structure [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) .

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
