---
description: Obtient le type d’élément dans le tableau.
title: 'IDebugArrayField :: GetElementType, | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9624a04ae70c8d29abd9b8af5b597b583efb7834
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143842"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
Obtient le type d’élément dans le tableau.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetElementType( 
   IDebugField** ppType
);
```

```csharp
int GetElementType(
   out IDebugField ppType
);
```

## <a name="parameters"></a>Paramètres
`ppType`\
à Retourne un objet [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) qui décrit le type d’élément.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 L’objet [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) part du principe que tous les éléments du tableau sont du même type.

## <a name="see-also"></a>Voir aussi
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
