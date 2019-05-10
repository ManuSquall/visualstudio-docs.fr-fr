---
title: TEXT_POSITION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TEXT_POSITION
helpviewer_keywords:
- TEXT_POSITION structure
ms.assetid: 6dcec574-a852-49fa-8c2e-2e71cbb5e3c6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 960fa95f583ddafdc401432ff551e8597fb956bd
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458345"
---
# <a name="textposition"></a>TEXT_POSITION
Décrit l’emplacement de colonne et de ligne dans le texte donné.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct _tagTEXT_POSITION { 
   DWORD dwLine;
   DWORD dwColumn;
} TEXT_POSITION;
```

```csharp
public struct TEXT_POSITION { 
   public uint dwLine;
   public uint dwColumn;
};
```

## <a name="members"></a>Membres

`dwLine`\

Index de ligne dans le fichier source.

`dwColumn`\

Offset de caractère dans la ligne.

## <a name="remarks"></a>Notes

Cette structure est utilisée dans le [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) et [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) structures.

Cette structure est remplie par un appel aux méthodes suivantes :

- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)

- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)

- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)

- [GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)

Cette structure est passée en tant que paramètre aux méthodes suivantes :

- [GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)

- [onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)

- [onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)

- [onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)

- [onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)

## <a name="requirements"></a>Configuration requise

 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi

- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)
- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
- [GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)
- [GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)