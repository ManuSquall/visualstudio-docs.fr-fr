---
description: Cette méthode récupère une liste de types d’arguments associés à cet objet.
title: 'IDebugBinder3 :: GetTypeArguments (| Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74cbd6e67a82113e43226ded8640630be50ba086
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102173895"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
Cette méthode récupère une liste de types d’arguments associés à cet objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetTypeArguments(
   UINT          skip,
   UINT          count,
   IDebugField** ppFields,
   UINT*         pFetched
);
```

```csharp
int GetTypeArguments(
   uint          skip,
   uint          count,
   IDebugField[] ppFields,
   out uint      pFetched
);
```

## <a name="parameters"></a>Paramètres
`skip`\
dans Nombre de champs à ignorer avant d’obtenir les types d’arguments.

`count`\
dans Nombre de champs d’arguments à retourner (spécifie également la taille du `ppFields` tableau).

`ppFields`\
[in, out] Tableau de champs qui seront remplis au retour de cette méthode.

`pFetched`\
[out] \( facultatif) nombre de champs de type d’argument réellement retournés.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Le nombre de types d’arguments peut être obtenu au préalable avec [GetTypeArgumentCount (](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md).

## <a name="see-also"></a>Voir aussi
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)
