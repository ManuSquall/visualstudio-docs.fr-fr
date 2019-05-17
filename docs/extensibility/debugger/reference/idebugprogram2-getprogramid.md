---
title: IDebugProgram2::GetProgramId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProgramId
helpviewer_keywords:
- IDebugProgram2::GetProgramId
ms.assetid: 2c31c0aa-2b71-46c7-849c-356e237d26f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a3dfec12193efda49a520a40418b93f2d4cef6b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870187"
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

#### <a name="parameters"></a>Paramètres
 `pguidProgramId`

 [out] Retourne le `GUID` pour ce programme.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Un moteur de débogage (dé) doit retourner l’identificateur de programme à l’origine passé à la [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) ou [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) méthodes. Ainsi, l’identification du programme sur le débogueur composants.

## <a name="see-also"></a>Voir aussi
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)