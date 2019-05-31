---
title: DOCCONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f31b33eeb782e71a87103d26a3bb78175611644e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318146"
---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
Spécifie les critères pour la comparaison de deux contextes de document.

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
Recherche le premier contexte de document dans la liste qui est égale au contexte de document cible.

`DOCCONTEXT_LESS_THAN`\
Recherche le premier contexte de document dans la liste qui est inférieur au contexte du document cible.

`DOCCONTEXT_GREATER_THAN`\
Recherche le premier contexte de document dans la liste qui est supérieure dans le contexte du document cible.

`DOCCONTEXT_SAME_DOCUMENT`\
Recherche le premier contexte de document dans la liste qui se trouve dans le même document que le contexte du document cible.

## <a name="remarks"></a>Notes
Passé en tant qu’argument à la [comparer](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) (méthode).

Ces valeurs sont utilisées pour spécifier des critères de comparaison pour trouver le premier contexte de document dans une liste. Un contexte de document reçoit une liste des contextes de document à comparer lui-même contre via le `IDebugDocumentContext2::Compare` (méthode). Le premier contexte de document dans la liste pour laquelle l’opérateur de comparaison est `true` est alors retournée.

## <a name="requirements"></a>Configuration requise
En-tête : msdbg.h

Espace de noms : Microsoft.VisualStudio.Debugger.Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
