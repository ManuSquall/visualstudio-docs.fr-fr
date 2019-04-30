---
title: IDebugBinder::ResolveRuntimeType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f1d4622e1de76406568cda4761005c5482f3169d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877495"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Cette méthode détermine le type au moment de l’exécution d’un objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ResolveRuntimeType( 
   IDebugObject* pObject,
   IDebugField** ppResolved
);
```

```csharp
int ResolveRuntimeType(
   IDebugObject     pObject,
   out IDebugField  ppResolved
);
```

#### <a name="parameters"></a>Paramètres
 `pObject`

 [in] Le [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) à résoudre.

 `ppResolved`

 [out] Retourne le type de l’objet comme un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Le type au moment de l’exécution d’un objet n’est pas toujours connu au moment de la compilation. Par exemple, l’utilisation du polymorphisme, un argument peut être passé à une fonction comme sa classe de base, tel qu’une classe de bouton. L’argument réel peut être une classe dérivée, tel qu’une classe de bouton radio.

## <a name="see-also"></a>Voir aussi
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)