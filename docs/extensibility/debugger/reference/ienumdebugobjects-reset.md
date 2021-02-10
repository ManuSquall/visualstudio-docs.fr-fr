---
title: 'IEnumDebugObjects :: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Reset
helpviewer_keywords:
- IEnumDebugObjects::Reset method
ms.assetid: 4a245e47-cc39-4177-b83d-083ea0e3190f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 39f2949a0c3b0c7009b17c8ceee09eee210c61cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957099"
---
# <a name="ienumdebugobjectsreset"></a>IEnumDebugObjects::Reset
Cette méthode réinitialise l’énumération au premier élément.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Reset(void);
```

```csharp
int Reset();
```

## <a name="parameters"></a>Paramètres
 None

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Après l’appel de cette méthode, l’appel suivant à [Next](../../../extensibility/debugger/reference/ienumdebugobjects-next.md) retourne le premier élément de l’énumération.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [Next](../../../extensibility/debugger/reference/ienumdebugobjects-next.md)
