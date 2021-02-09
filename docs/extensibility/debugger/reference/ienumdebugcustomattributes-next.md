---
title: 'IEnumDebugCustomAttributes :: suivant | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Next
helpviewer_keywords:
- IEnumDebugCustomAttributes::Next
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2eefa444d1832e4f66aac161636177994bd4a51f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929260"
---
# <a name="ienumdebugcustomattributesnext"></a>IEnumDebugCustomAttributes::Next
Récupère un nombre spécifié d’attributs personnalisés dans une séquence d’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Next ( 
   ULONG      celt,
   CODE_PATH* rgelt,
   ULONG*     pceltFetched
);
```

```csharp
int Next(
   uint                        celt,
   out IDebugCustomAttribute[] rgelt,
   ref uint                    pceltFetched
);
```

## <a name="parameters"></a>Paramètres
`celt`\
[in] Nombre d'éléments à récupérer. Spécifie également la taille maximale du `rgelt` tableau.

`rgelt`\
à Tableau d’objets [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) à remplir.

`pceltFetched`\
à Retourne le nombre d’éléments réellement retournés dans `rgelt` .

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si un nombre inférieur au nombre d’éléments demandés peut être retourné ; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
