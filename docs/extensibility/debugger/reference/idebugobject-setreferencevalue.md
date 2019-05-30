---
title: IDebugObject::SetReferenceValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aaef4eb96942789bd3f574e6eeddcd3500ae6ee9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349959"
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Définit la valeur de référence de cet objet.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetReferenceValue( 
   IDebugObject* pObject
);
```

```csharp
int SetReferenceValue(
   [In] IDebugObject pObject
);
```

## <a name="parameters"></a>Paramètres
`pObject`\
[in] Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objet représentant la nouvelle valeur de référence.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode effectue cela [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) une référence à la valeur de l’objet indiqué dans l’objet le `pObject` paramètre, en supprimant toutes les références précédentes. Notez que ce `IDebugObject` objet doit être déjà d’un type référence.

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)