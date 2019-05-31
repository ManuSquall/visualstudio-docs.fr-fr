---
title: IDebugField::GetTypeInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fc48442e27315e289c812c14e0ae70d8b8fd437a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333116"
---
# <a name="idebugfieldgettypeinfo"></a>IDebugField::GetTypeInfo
Cette méthode obtient indépendant du type d’informations sur le symbole ou d’un type.

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
[out] Retourne les informations de type dans la liste fournie [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) structure.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Indépendant du type informations inclut, par exemple, le domaine d’application, le module et la classe qui contient le symbole.

## <a name="see-also"></a>Voir aussi
- [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)