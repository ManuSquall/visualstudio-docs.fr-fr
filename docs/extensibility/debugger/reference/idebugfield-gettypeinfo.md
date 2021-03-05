---
description: Cette méthode obtient des informations indépendantes du type sur le symbole ou le type.
title: 'IDebugField :: GetTypeInfo | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e908fb4eec16ec9891eda5127c753616419fc176
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151868"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Cette méthode obtient des informations indépendantes du type sur le symbole ou le type.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetTypeInfo( 
   TYPE_INFO* pTypeInfo
);
```

```csharp
int GetTypeInfo(
   TYPE_INFO[] pTypeInfo
);
```

## <a name="parameters"></a>Paramètres
`pTypeInfo`\
à Retourne des informations de type dans la structure [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) fournie.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Les informations indépendantes du type incluent, par exemple, AppDomain, le module et la classe qui contient le symbole.

## <a name="see-also"></a>Voir aussi
- [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
