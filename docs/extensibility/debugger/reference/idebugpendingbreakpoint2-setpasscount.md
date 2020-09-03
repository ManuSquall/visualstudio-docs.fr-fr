---
title: 'IDebugPendingBreakpoint2 :: SetPassCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 732eadc955b9a6c9bdded3d52f038ff58ed9c217
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725678"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Définit ou modifie le nombre de réussites associé au point d’arrêt en attente.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Paramètres
`bpPassCount`\
dans Structure [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) qui contient le nombre de passes.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur. Retourne `E_BP_DELETED` si le point d’arrêt a été supprimé.

## <a name="remarks"></a>Notes
 Tout nombre de réussites précédemment associé au point d’arrêt en attente est perdu. Tous les points d’arrêt liés à ce point d’arrêt en attente sont appelés pour définir leur nombre de passes sur le `bpPassCount` paramètre.

## <a name="see-also"></a>Voir aussi
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
