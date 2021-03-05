---
description: Spécifie les critères de comparaison de deux contextes de mémoire.
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 70f4621eaad5e494684e6c227959e13566a22eba
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102170781"
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
Recherche le premier contexte de mémoire dans la liste qui est égal au contexte de mémoire cible.

`CONTEXT_LESS_THAN`\
Recherche le premier contexte de mémoire dans la liste qui est inférieur au contexte de mémoire cible.

`CONTEXT_GREATER_THAN`\
Recherche le premier contexte de mémoire dans la liste qui est supérieur au contexte de mémoire cible.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Recherche le premier contexte de mémoire dans la liste qui est inférieur ou égal au contexte de mémoire cible.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Recherche le premier contexte de mémoire dans la liste qui est supérieur ou égal au contexte de mémoire cible.

`CONTEXT_SAME_SCOPE`\
Recherche le premier contexte de mémoire dans la liste qui se trouve dans la même portée que le contexte de mémoire cible.

`CONTEXT_SAME_FUNCTION`\
Recherche le premier contexte de mémoire dans la liste qui se trouve dans la même fonction que la portée de la mémoire cible.

`CONTEXT_SAME_MODULE`\
Recherche le premier contexte de mémoire dans la liste qui se trouve dans le même module que le contexte de mémoire cible.

`CONTEXT_SAME_PROCESS`\
Recherche le premier contexte de mémoire dans la liste qui se trouve dans le même processus que le contexte de mémoire cible.

## <a name="remarks"></a>Notes
Passé comme argument à la méthode [compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) .

Ces valeurs sont utilisées pour rechercher le premier contexte de mémoire dans une liste qui répond aux critères de comparaison spécifiés. Un contexte de mémoire reçoit une liste de contextes de mémoire à comparer par rapport à la `IDebugMemoryContext2::Compare` méthode. Le premier contexte de mémoire dans la liste pour lequel l’opérateur de comparaison est `true` alors retourné.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
