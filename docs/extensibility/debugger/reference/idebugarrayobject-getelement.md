---
title: 'IDebugArrayObject :: GetElement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e29fe09905119057224b45b455e4f56e5ce904af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80736171"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Obtient un élément du tableau.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>Paramètres
`dwIndex`\
dans Index de l’élément.

`ppElement`\
à Retourne une interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente l’élément.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode voit tous les éléments d’un objet tableau sous la forme d’un tableau unidimensionnel, même si l’objet tableau est multidimensionnel. Par exemple, étant donné le tableau `myarray[3][2][6]` et un `dwIndex` paramètre de 20, cette méthode retourne l’élément à partir de `myarray[1][1][2]` , et un `dwIndex` paramètre de 21 retourne l’élément à partir de `myarray[1][1][3]` . Utilisez la méthode [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) pour déterminer le nombre total d’éléments dans le tableau.

## <a name="see-also"></a>Voir aussi
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
