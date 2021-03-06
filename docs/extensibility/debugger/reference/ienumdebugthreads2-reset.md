---
description: Rétablit l’énumération threads sur le premier élément.
title: 'IEnumDebugThreads2 :: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Reset
helpviewer_keywords:
- IEnumDebugThreads2::Reset
ms.assetid: 88980d9a-c4d6-4de4-a9ab-fb56fa71394a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1521e69b5896422a811714be9e4aefa649824ab4
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225784"
---
# <a name="ienumdebugthreads2reset"></a>IEnumDebugThreads2::Reset
Réinitialise l'énumération au premier élément.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Une fois cette méthode appelée, le prochain appel à la méthode [suivante](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md) retourne le premier élément de l’énumération.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
