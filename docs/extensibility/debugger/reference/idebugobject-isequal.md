---
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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13018e31fb5f8bed89a0a290d687360a605a855d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726504"
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
