---
title: IDebugProperty2::GetDerivedMostProperty (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2086aded4361049d722ec36ba1d470ed8f7ac6e5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721507"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Obtient la propriété dérivée-la plus d’une propriété.

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
[out] Retourne un objet [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) qui représente la propriété la plus dérivée.

## <a name="return-value"></a>Valeur de retour
 En cas `S_OK`de succès, les retours; retourne autrement le code d’erreur. Retours `S_GETDERIVEDMOST_NO_DERIVED_MOST` s’il n’y a pas de biens dérivés les plus à récupérer.

## <a name="remarks"></a>Notes
 Par exemple, si cette propriété décrit `ClassRoot` un objet qui implémente `ClassDerived` mais `ClassRoot`qui est en fait une instantanéisation de ce `ClassDerived` qui est dérivé , alors cette méthode renvoie un objet [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) décrivant l’objet.

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
