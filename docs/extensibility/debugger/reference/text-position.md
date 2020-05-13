---
title: TEXT_POSITION Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TEXT_POSITION
helpviewer_keywords:
- TEXT_POSITION structure
ms.assetid: 6dcec574-a852-49fa-8c2e-2e71cbb5e3c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1a36c585a09afbd1dec60e1d4399dca258399ae3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713408"
---
# <a name="text_position"></a>TEXT_POSITION
Décrit l’emplacement de la ligne et de la colonne dans le texte donné.

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
Index de la ligne dans le fichier source.

`dwColumn`\
Caractère décalé en ligne.

## <a name="remarks"></a>Notes

Cette structure est utilisée dans les structures [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) et [de démontageData.](../../../extensibility/debugger/reference/disassemblydata.md)

Cette structure est remplie par un appel aux méthodes suivantes :

- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)

- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)

- [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)

- [GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)

Cette structure est transmise comme un paramètre aux méthodes suivantes :

- [GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)

- [onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)

- [onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)

- [onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)

- [onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)

## <a name="requirements"></a>Spécifications

 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

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
