---
description: Spécifie les critères de comparaison de deux contextes de document.
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6eeee3e31c898660930b676df716fe25769bbb8b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105096003"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
Spécifie les critères de comparaison de deux contextes de document.

## <a name="syntax"></a>Syntaxe

```cpp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
typedef DWORD DOCCONTEXT_COMPARE;
```

```csharp
enum enum_DOCCONTEXT_COMPARE {
    DOCCONTEXT_EQUAL         = 0x0001,
    DOCCONTEXT_LESS_THAN     = 0x0002,
    DOCCONTEXT_GREATER_THAN  = 0x0003,
    DOCCONTEXT_SAME_DOCUMENT = 0x0004
};
```

## <a name="fields"></a>Champs
`DOCCONTEXT_EQUAL`\
Recherche le premier contexte de document dans la liste qui est égal au contexte du document cible.

`DOCCONTEXT_LESS_THAN`\
Recherche le premier contexte de document dans la liste qui est inférieur au contexte du document cible.

`DOCCONTEXT_GREATER_THAN`\
Recherche le premier contexte de document dans la liste qui est supérieur au contexte du document cible.

`DOCCONTEXT_SAME_DOCUMENT`\
Recherche le premier contexte de document dans la liste qui se trouve dans le même document que le contexte de document cible.

## <a name="remarks"></a>Notes
Passé comme argument à la méthode [compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) .

Ces valeurs sont utilisées pour spécifier des critères de comparaison pour rechercher le premier contexte de document dans une liste. Un contexte de document reçoit une liste de contextes de document à comparer par rapport à la `IDebugDocumentContext2::Compare` méthode. Le premier contexte de document dans la liste pour lequel l’opérateur de comparaison est `true` est ensuite retourné.

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
