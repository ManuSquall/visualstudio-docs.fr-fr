---
title: CONTEXT_COMPARE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c88b50644d1adda2dd0eaa3b74a828f9739d70b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737609"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
Spécifie les critères de comparaison de deux contextes de mémoire.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
typedef DWORD CONTEXT_COMPARE;
```

```csharp
public enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
```

## <a name="fields"></a>Champs
`CONTEXT_EQUAL`\
Trouvez le premier contexte de mémoire dans la liste qui est égal au contexte de mémoire cible.

`CONTEXT_LESS_THAN`\
Trouvez le premier contexte de mémoire dans la liste qui est inférieur au contexte de mémoire cible.

`CONTEXT_GREATER_THAN`\
Trouvez le premier contexte de mémoire dans la liste qui est plus grand que le contexte de mémoire cible.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Trouvez le premier contexte de mémoire dans la liste qui est inférieur ou égal au contexte de mémoire cible.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Trouvez le premier contexte de mémoire dans la liste qui est supérieur ou égal au contexte de mémoire cible.

`CONTEXT_SAME_SCOPE`\
Trouvez le premier contexte de mémoire dans la liste qui est dans la même portée que le contexte de mémoire cible.

`CONTEXT_SAME_FUNCTION`\
Trouvez le premier contexte de mémoire dans la liste qui est dans la même fonction que la portée de mémoire cible.

`CONTEXT_SAME_MODULE`\
Trouvez le premier contexte de mémoire dans la liste qui est dans le même module que le contexte de mémoire cible.

`CONTEXT_SAME_PROCESS`\
Trouvez le premier contexte de mémoire dans la liste qui est dans le même processus que le contexte de mémoire cible.

## <a name="remarks"></a>Notes
Passé comme argument à la méthode [Compare.](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)

Ces valeurs sont utilisées pour trouver le premier contexte de mémoire dans une liste qui satisfait les critères de comparaison spécifiés. Un contexte de mémoire est donné une liste de `IDebugMemoryContext2::Compare` contextes de mémoire pour se comparer à travers la méthode. Le premier contexte de mémoire dans la `true` liste pour laquelle l’opérateur de comparaison est est ensuite retourné.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
