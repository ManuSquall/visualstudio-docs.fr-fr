---
title: 'IDebugProperty2 :: GetDerivedMostProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f91b00d2f448aea2f187e37813782ce568ad859
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916038"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Obtient la propriété la plus dérivée d’une propriété.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDerivedMostProperty ( 
   IDebugProperty2** ppDerivedMost
);
```

```csharp
int GetDerivedMostProperty ( 
   out IDebugProperty2 ppDerivedMost
);
```

## <a name="parameters"></a>Paramètres
`ppDerivedMost`\
à Retourne un objet [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente la propriété la plus dérivée.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur. Retourne `S_GETDERIVEDMOST_NO_DERIVED_MOST` s’il n’existe aucune propriété la plus dérivée à récupérer.

## <a name="remarks"></a>Notes
 Par exemple, si cette propriété décrit un objet qui implémente `ClassRoot` , mais qui est en fait une instanciation de `ClassDerived` qui est dérivée de `ClassRoot` , cette méthode retourne un objet [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) décrivant l' `ClassDerived` objet.

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
