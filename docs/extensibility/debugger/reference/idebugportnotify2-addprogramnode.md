---
description: Inscrit un programme pouvant être débogué avec le port sur lequel il s’exécute.
title: 'IDebugPortNotify2 :: AddProgramNode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2::AddProgramNode
helpviewer_keywords:
- IDebugPortNotify2::AddProgramNode
ms.assetid: 34c0e949-1eb9-4108-9cb8-a3eb87fcf190
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 186bfbfd44a88450aeade264020f70e0eddc7fb8
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102142581"
---
# <a name="idebugportnotify2addprogramnode"></a>IDebugPortNotify2::AddProgramNode
Inscrit un programme pouvant être débogué avec le port sur lequel il s’exécute.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT AddProgramNode( 
   IDebugProgramNode2* pProgramNode
);
```

```csharp
int AddProgramNode( 
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Paramètres
`pProgramNode`\
dans Objet [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui représente le programme à inscrire.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Un nœud de programme peut être désinscrit du port en appelant la méthode [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)
