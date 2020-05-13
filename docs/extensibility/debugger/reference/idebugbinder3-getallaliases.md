---
title: IDebugBinder3:GetAllAliases ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d512fa6eb7529e11c766d7c173b318aa6f8f2f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735807"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Cette méthode récupère une liste d’alias du programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>Paramètres
`uRequest`\
[dans] Le nombre maximum d’alias à retourner (précise la `ppAliases`longueur du tableau passé dans ).

`ppAliases`\
[dans, dehors] Array pour remplir avec des alias (si `uRequest` c’est une valeur nulle et est de 0, le nombre d’alias qui peuvent être retournés sera retourné par `puFetched`).

`puFetched`\
[out] Retourne le nombre d’alias obtenus.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
