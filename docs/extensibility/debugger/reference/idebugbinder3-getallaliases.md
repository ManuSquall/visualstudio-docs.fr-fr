---
description: Cette méthode récupère une liste d’alias à partir du programme.
title: 'IDebugBinder3 :: GetAllAliases | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16a9d41280a9ff97072390a0cd2e687ee24e1d83
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102174045"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Cette méthode récupère une liste d’alias à partir du programme.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

## <a name="parameters"></a>Paramètres
`uRequest`\
dans Nombre maximal d’alias à retourner (spécifie la longueur du tableau passé à `ppAliases` ).

`ppAliases`\
[in, out] Tableau à remplir avec des alias (s’il s’agit d’une valeur null et `uRequest` est égal à 0, le nombre d’alias qui peuvent être retournés est retourné par `puFetched` ).

`puFetched`\
à Retourne le nombre d’alias obtenus.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
