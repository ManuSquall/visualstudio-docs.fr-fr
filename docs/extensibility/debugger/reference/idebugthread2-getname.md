---
title: IDebugThread2::GetName ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetName
helpviewer_keywords:
- IDebugThread2::GetName
ms.assetid: eec54b8f-4a0e-4919-b0f9-81d4bd1e0b6f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d4828b573585969154f2ad1d484c9fcdf767417
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718772"
---
# <a name="idebugthread2getname"></a>IDebugThread2::GetName
Obtient le nom d’un fil.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetName ( 
   BSTR* pbstrName
);
```

```csharp
int GetName ( 
   out string pbstrName
);
```

## <a name="parameters"></a>Paramètres
`pbstrName`\
[out] Retourne le nom du fil.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le nom récupéré est toujours un nom qui peut être affiché et ce nom décrit le fil. Le nom de fil peut être dérivé d’une architecture de temps d’exécution qui prend en charge les fils nommés, ou il pourrait être un nom dérivé du moteur de déboguer. Alternativement, le nom du thread peut être défini par un appel à la méthode [SetThreadName.](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)

## <a name="see-also"></a>Voir aussi
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [SetThreadName](../../../extensibility/debugger/reference/idebugthread2-setthreadname.md)
