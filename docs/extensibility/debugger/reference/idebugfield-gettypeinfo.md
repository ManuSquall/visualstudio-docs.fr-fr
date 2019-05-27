---
title: IDebugField::GetTypeInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetTypeInfo
helpviewer_keywords:
- IDebugField::GetTypeInfo method
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 781c9a0e4365a454d45af957207099d6d5ae7d92
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212657"
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