---
description: Teste si cet objet est une référence null.
title: 'IDebugObject :: IsNullReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsNullReference
helpviewer_keywords:
- IDebugObject::IsNullReference method
ms.assetid: 6dbfcdb0-954f-4486-8fac-7ea8d003e3a9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba037f995c97a3bfbf059f51bfb4f8777803a172
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054073"
---
# <a name="idebugobjectisnullreference"></a>IDebugObject::IsNullReference
Teste si cet objet est une référence null.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsNullReference( 
   BOOL* pfIsNull
);
```

```csharp
int IsNullReference(
   out int pfIsNull
);
```

## <a name="parameters"></a>Paramètres
`pfIsNull`\
à Retourne une valeur différente de zéro ( `TRUE` ) si cet objet est une référence null ; sinon, retourne zéro ( `FALSE` ).

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Une référence null signifie un objet vide ou un objet qui n’a pas été assigné à.

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
