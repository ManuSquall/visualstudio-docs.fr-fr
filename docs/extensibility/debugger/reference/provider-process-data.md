---
title: PROVIDER_PROCESS_DATA Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROVIDER_PROCESS_DATA
helpviewer_keywords:
- PROVIDER_PROCESS_DATA structure
ms.assetid: ec2362ed-4a0c-4a09-9d66-8ff04e4f41ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdaf15d09af3199d026155cf7667f063f5bbe858
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713776"
---
# <a name="provider_process_data"></a>PROVIDER_PROCESS_DATA
Cette structure fournit des informations sur les processus fonctionnant sur une machine.

## <a name="syntax"></a>Syntaxe

```cpp
typedef struct tagPROVIDER_PROCESS_DATA {
   PROVIDER_FIELDS    Fields;
   PROGRAM_NODE_ARRAY ProgramNodes;
   BOOL               fIsDebuggerPresent;
} PROVIDER_PROCESS_DATA;
```

```csharp
public struct PROVIDER_PROCESS_DATA {
   public uint               Fields;
   public PROGRAM_NODE_ARRAY ProgramNodes;
   public int                fIsDebuggerPresent;
}
```

## <a name="members"></a>Membres
 `Fields`\
 Une combinaison de drapeaux de [l’PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md) recensement, indiquant quels champs sont remplis.

 `ProgramNodes`\
 Une structure [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) qui contient un éventail de nœuds de programme.

 `fIsDebuggerPresent`\
 Nonzero`TRUE`( ) [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] si le débbuggeur`FALSE`est en cours d’exécution, zéro ( ) si elle n’est pas.

## <a name="remarks"></a>Notes
 Cette structure est transmise à la méthode [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) où elle est remplie.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Structures et unions](../../../extensibility/debugger/reference/structures-and-unions.md)
- [PROVIDER_FIELDS](../../../extensibility/debugger/reference/provider-fields.md)
- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
