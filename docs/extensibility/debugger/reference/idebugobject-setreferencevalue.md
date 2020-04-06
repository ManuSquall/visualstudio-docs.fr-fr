---
title: IDebugObject::SetReferenceValue - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cc0db8ee7f0581a4c336111d3876c24f0e5c12d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726380"
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
[dans] Un objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) représentant la nouvelle valeur de référence.

## <a name="return-value"></a>Valeur de retour
 En cas de succès, les retours S_OK; autrement, renvoie un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode fait de cet objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) une référence `pObject` à la valeur de l’objet donné dans le paramètre, jetant toute référence précédente. Notez `IDebugObject` que cet objet doit déjà être un type de référence.

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
