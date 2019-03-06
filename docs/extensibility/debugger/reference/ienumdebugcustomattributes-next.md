---
title: IEnumDebugCustomAttributes::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Next
helpviewer_keywords:
- IEnumDebugCustomAttributes::Next
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fdad468c788d475d32eddca160728b2c3ecf11d9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56683713"
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

#### <a name="parameters"></a>Paramètres
 `celt`

 [in] Le nombre d’éléments à récupérer. Spécifie également la taille maximale de la `rgelt` tableau.

 `rgelt`

 [out] Un tableau de [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) objets doit être renseigné.

 `pceltFetched`

 [out] Retourne le nombre d’éléments réellement retournés dans `rgelt`.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`. Retourne `S_FALSE` si inférieur au nombre demandé d’éléments peut être retournés ; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)