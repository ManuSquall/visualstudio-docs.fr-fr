---
description: Définit la valeur de référence de cet objet.
title: 'IDebugObject :: SetReferenceValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5a65c14d4122ac6d877573822b4fa8be1cb6cdd1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054112"
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
dans Objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) qui représente la nouvelle valeur de référence.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Cette méthode fait en sorte que cet objet [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) fasse référence à la valeur de l’objet donné dans le `pObject` paramètre, en levant toute référence précédente. Notez que cet `IDebugObject` objet doit déjà être un type référence.

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
