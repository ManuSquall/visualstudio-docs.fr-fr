---
description: Annule l’inscription d’un programme pouvant être débogué à partir du port sur lequel il s’exécute.
title: 'IDebugPortNotify2 :: RemoveProgramNode | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2::RemoveProgramNode
helpviewer_keywords:
- IDebugPortNotify2::RemoveProgramNode
ms.assetid: 3668157b-66d2-416e-a359-fc04dcd18a48
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 10208570237de10f9a6e682fc3a7478bd15ca24d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072414"
---
# <a name="idebugportnotify2removeprogramnode"></a>IDebugPortNotify2::RemoveProgramNode
Annule l’inscription d’un programme pouvant être débogué à partir du port sur lequel il s’exécute.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT RemoveProgramNode( 
   IDebugProgramNode2* pProgramNode
);
```

```csharp
int RemoveProgramNode( 
   IDebugProgramNode2 pProgramNode
);
```

## <a name="parameters"></a>Paramètres
`pProgramNode`\
dans [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objecy qui représente le programme dont l’inscription doit être annulée.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode supprime un nœud de programme qui a été ajouté avec un appel à la méthode [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) .

## <a name="see-also"></a>Voir aussi
- [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
