---
title: 'IDebugProgram2 :: GetProgramId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bb172f48b63ef2ec182f1a83d599a91eff1e2ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722772"
---
# <a name="idebugprogram2getprogramid"></a>IDebugProgram2::GetProgramId
Obtient un GUID pour ce programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProgramId( 
   GUID* pguidProgramId
);
```

```csharp
int GetProgramId( 
   out Guid pguidProgramId
);
```

## <a name="parameters"></a>Paramètres
`pguidProgramId`\
à Retourne le `GUID` pour ce programme.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Un moteur DE débogage (DE) doit retourner l’identificateur de programme initialement passé aux méthodes [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) ou [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) . Cela permet d’identifier le programme parmi les composants du débogueur.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)
