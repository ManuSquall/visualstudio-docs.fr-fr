---
description: Obtient le nombre d’éléments dans le tableau.
title: 'IDebugArrayObject :: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4dafff955eb0801ffe13f76f61d8f7451398e41e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158694"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Obtient le nombre d’éléments dans le tableau.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>Paramètres
`pdwElements`\
à Retourne le nombre.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode voit tous les éléments d’un objet tableau sous la forme d’un tableau unidimensionnel, même si l’objet tableau est multidimensionnel. Par exemple, étant donné le tableau `myarray[3][2][6]` , cette méthode retourne 36 dans le `pdwElements` paramètre. Utilisez la méthode [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) pour récupérer individuellement les éléments un par un.

## <a name="see-also"></a>Voir aussi
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
