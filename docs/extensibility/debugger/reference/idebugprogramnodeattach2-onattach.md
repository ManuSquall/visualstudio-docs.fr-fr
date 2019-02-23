---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c79f15102b5adae2112f4abdeeb68b80962895e8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701522"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Est attaché au programme associé ou diffère le processus d’attachement à la [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) (méthode).

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

#### <a name="parameters"></a>Paramètres
 `guidProgramId`

 [in] `GUID` à affecter au programme associé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si le [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) méthode ne doit pas être appelée. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est appelée pendant le processus d’attachement, avant le [attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md) méthode est appelée. Le `OnAttach` méthode peut exécuter le processus d’attachement lui-même (dans ce cas, cette méthode retourne `S_FALSE`) ou différer le processus d’attachement à la `IDebugEngine2::Attach` (méthode) (le `OnAttach` retourne de la méthode `S_OK`). Dans les deux cas, le `OnAttach` méthode peut définir le `GUID` du programme en cours de débogage à la donnée `GUID`.

## <a name="see-also"></a>Voir aussi
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attacher](../../../extensibility/debugger/reference/idebugengine2-attach.md)