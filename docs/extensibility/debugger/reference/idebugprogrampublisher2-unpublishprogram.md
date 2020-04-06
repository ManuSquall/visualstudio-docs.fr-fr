---
title: IDebugProgramPublisher2::UnpublishProgram (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fa3d111559a2c82fe36def202e5c1cf120c5202
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721590"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Rend un programme indisponible pour être débogé.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT UnpublishProgram(
   IUnknown* pDebuggeeInterface
);
```

```csharp
int UnpublishProgram(
   object pDebuggeeInterface
);
```

## <a name="parameters"></a>Paramètres
`pDebuggeeInterface`\
[dans] Une `IUnknown` interface au programme. Il s’agit de la même valeur fournie à la méthode [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) et identifie uniquement le programme supprimé (c’est-à-dire qu’il est utilisé comme cookie).

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Pour mettre un programme à la disposition des moteurs de débogé et du gestionnaire de débogé de session, utilisez la méthode [PublishProgram.](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)

## <a name="see-also"></a>Voir aussi
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
