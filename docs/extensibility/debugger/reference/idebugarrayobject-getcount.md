---
title: IDebugArrayObject::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac21ac30e1f4511efa1ec8a7fe27129bf2ddb3a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321661"
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
[out] Retourne le nombre.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode voit tous les éléments d’un objet tableau comme un tableau unidimensionnel, même si l’objet de tableau est multidimensionnel. Par exemple, étant donné le tableau `myarray[3][2][6]`, cette méthode retourne 36 dans le `pdwElements` paramètre. Utilisez le [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) méthode pour récupérer les éléments individuels d’un à la fois.

## <a name="see-also"></a>Voir aussi
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)