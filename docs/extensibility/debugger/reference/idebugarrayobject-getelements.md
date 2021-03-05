---
description: Obtient un énumérateur de tous les éléments du tableau.
title: 'IDebugArrayObject :: GetElements | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33840f3f5d5a65cf1ed929049f0b85801724a5c9
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158551"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Obtient un énumérateur de tous les éléments du tableau.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>Paramètres
`ppEnum`\
à Retourne un objet [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) qui autorise l’énumération de tous les éléments.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Vous pouvez également utiliser les méthodes [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) et [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) pour itérer au sein des éléments.

## <a name="see-also"></a>Voir aussi
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
