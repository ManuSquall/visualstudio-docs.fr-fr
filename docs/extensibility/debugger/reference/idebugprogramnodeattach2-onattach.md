---
title: IDebugProgramNodeAttach2::OnAttach Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dfb8a39af3c030dadddcb148a79a96b57f20e183
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721879"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
Attache au programme associé ou reporte le processus d’attachement à la méthode [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

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

## <a name="parameters"></a>Paramètres
`guidProgramId`\
[dans] `GUID` d’attribuer au programme associé.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si la méthode [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) ne doit pas être appelée. Sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode est appelée pendant le processus de fixation, avant que la méthode [d’attachement](../../../extensibility/debugger/reference/idebugengine2-attach.md) soit appelée. La `OnAttach` méthode peut effectuer le processus d’attachement `S_FALSE`lui-même (dans ce `IDebugEngine2::Attach` cas, `OnAttach` cette `S_OK`méthode retourne ) ou reporter le processus d’attachement à la méthode (la méthode retourne ). Dans les deux `OnAttach` cas, `GUID` la méthode peut définir le programme `GUID`étant débogé à la donnée .

## <a name="see-also"></a>Voir aussi
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
