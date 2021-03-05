---
description: Compare un objet à cet objet.
title: 'IDebugObject :: IsEqual | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0907b72f2a0647fc6ff6181ecdc5c7fd8c2134cb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151660"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Compare un objet à cet objet.

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
dans Objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant l’objet à comparer.

`pfIsEqual`\
à Retourne une valeur différente de zéro ( `TRUE` ) si les valeurs des objets sont égales ; sinon, retourne la valeur zéro ( `FALSE` ).

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 En règle générale, cette méthode peut comparer les adresses des valeurs représentées par le `pObject` paramètre et cet objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ; si les adresses sont égales, les objets peuvent être considérés comme égaux.

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
