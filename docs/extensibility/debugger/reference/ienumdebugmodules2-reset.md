---
title: 'IEnumDebugModules2 :: Reset | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Reset
helpviewer_keywords:
- IEnumDebugModules2::Reset
ms.assetid: f6ff364c-2644-4919-b950-3cb82eb6f601
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81fc33620449837f3d2af883f0721d24df92e804
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716517"
---
# <a name="ienumdebugmodules2reset"></a>IEnumDebugModules2::Reset
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
 Une fois cette méthode appelée, le prochain appel à la méthode [suivante](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md) retourne le premier élément de l’énumération.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
