---
title: 'IDebugPortEx2 :: GetProgram | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::GetProgram
helpviewer_keywords:
- IDebugPortEx2::GetProgram
ms.assetid: cd83a111-bfd5-4eae-b576-526466c6b6ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f1f9dea8706b8075b460b813d2dc58a916198d37
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725091"
---
# <a name="idebugportex2getprogram"></a>IDebugPortEx2::GetProgram
Obtient le programme associé à un nœud de programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProgram( 
   IDebugProgramNode2* pProgramNode,
   IDebugProgram2**    ppProgram
);
```

```csharp
int GetProgram( 
   IDebugProgramNode2 pProgramNode,
   out IDebugProgram2 ppProgram
);
```

## <a name="parameters"></a>Paramètres
`pProgramNode` dans Objet [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui représente le nœud de programme.

`ppProgram` à Retourne un objet [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) qui représente le programme associé au nœud de programme.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
