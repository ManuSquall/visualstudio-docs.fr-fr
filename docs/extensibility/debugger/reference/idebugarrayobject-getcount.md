---
title: IDebugArrayObject::GetCount ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9d5e322b7bcd5238335c74caa21989f1f1962ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736199"
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
[out] Retourne le compte.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode voit tous les éléments d’un objet de tableau comme un tableau unidimensionnel, même si l’objet de tableau est multidimensionnel. Par exemple, compte `myarray[3][2][6]`tenu du tableau, cette `pdwElements` méthode retournerait 36 dans le paramètre. Utilisez la méthode [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) pour récupérer les éléments individuels un à la fois.

## <a name="see-also"></a>Voir aussi
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
