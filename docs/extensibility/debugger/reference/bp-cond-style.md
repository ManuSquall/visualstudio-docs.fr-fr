---
title: BP_COND_STYLE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_COND_STYLE
helpviewer_keywords:
- BP_COND_STYLE enumeration
ms.assetid: a93b1412-f447-48a1-af9d-38f3dbb3092f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca704ca186308ea9e44c4fa7edc6617cbac806eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738117"
---
# <a name="bp_cond_style"></a>BP_COND_STYLE
Spécifie le style d’état de point d’arrêt pour les points d’arrêt en attente et liés.

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
Allume le point d’arrêt lorsque la position du point d’arrêt est atteinte. Aucune condition de point d’arrêt spécifiée.

`BP_COND_WHEN_TRUE`\
Les feux du point d’arrêt seulement lorsque l’expression conditionnelle associée au point d’arrêt s’évalue à `true`.

`BP_COND_WHEN_CHANGED`\
Le point d’arrêt n’est le point d’arrêt que lorsque la valeur de l’expression conditionnelle associée au point d’arrêt a changé par rapport à son évaluation précédente.

## <a name="remarks"></a>Notes
Utilisé pour `styleCondition` le membre de la structure [BP_CONDITION.](../../../extensibility/debugger/reference/bp-condition.md)

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
