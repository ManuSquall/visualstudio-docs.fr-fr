---
title: DOCCONTEXT_COMPARE Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75e4453cae63f484961cb2d0f3385a703709f83b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737233"
---
# <a name="doccontext_compare"></a>DOCCONTEXT_COMPARE
Spécifie les critères de comparaison de deux contextes documentaires.

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
Trouvez le premier contexte de document dans la liste qui est égal au contexte du document cible.

`DOCCONTEXT_LESS_THAN`\
Trouvez le premier contexte de document dans la liste qui est inférieur au contexte du document cible.

`DOCCONTEXT_GREATER_THAN`\
Trouvez le premier contexte de document dans la liste qui est supérieur au contexte du document cible.

`DOCCONTEXT_SAME_DOCUMENT`\
Trouvez le premier contexte de document dans la liste qui se trouve dans le même document que le contexte du document cible.

## <a name="remarks"></a>Notes
Passé comme argument à la méthode [Compare.](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)

Ces valeurs sont utilisées pour spécifier un critère de comparaison pour trouver le premier contexte de document dans une liste. Un contexte de document est donné une liste de `IDebugDocumentContext2::Compare` contextes de documents pour se comparer à travers la méthode. Le premier contexte de document dans la `true` liste pour laquelle l’opérateur comparatif est est ensuite retourné.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
