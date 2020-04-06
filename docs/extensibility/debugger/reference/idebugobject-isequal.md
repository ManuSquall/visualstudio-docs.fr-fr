---
title: IDebugObject::IsEqual Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13018e31fb5f8bed89a0a290d687360a605a855d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726504"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Compare un objet avec cet objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsEqual( 
   IDebugObject* pObject,
   BOOL*         pfIsEqual
);
```

```csharp
int IsEqual(
   IDebugObject pObject,
   out int      pfIsEqual
);
```

## <a name="parameters"></a>Paramètres
`pObject`\
[dans] Un objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant l’objet à comparer.

`pfIsEqual`\
[out] Retourne non-zéro`TRUE`( ) si les valeurs des objets sont égales; autrement, retourne`FALSE`zéro ( ).

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Typiquement, cette méthode peut comparer les adresses `pObject` des valeurs représentées par le paramètre et cet objet [IDebugObject;](../../../extensibility/debugger/reference/idebugobject.md) si les adresses sont égales, alors les objets peuvent être considérés comme égaux.

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
