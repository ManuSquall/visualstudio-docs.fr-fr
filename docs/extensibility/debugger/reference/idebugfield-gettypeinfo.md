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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9ea120cb58faa28bbb8168800ef6e35f707d879f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073701"
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
