---
description: Détermine si cet objet est en lecture seule.
title: 'IDebugObject :: IsReadOnly | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0b3cf66d8d540a92b937de996368ed24b18ae0b8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054060"
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Détermine si cet objet est en lecture seule.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsReadOnly( 
   BOOL* pfIsReadOnly
);
```

```csharp
int IsReadOnly(
   out int pfIsReadOnly
);
```

## <a name="parameters"></a>Paramètres
`pfIsReadOnly`\
à Retourne une valeur différente de zéro ( `TRUE` ) si cet objet est en lecture seule ; sinon, retourne la valeur zéro ( `FALSE` ).

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne S_OK ; Sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 La valeur d’un objet en lecture seule ne peut pas être modifiée une fois qu’il a été créé.

## <a name="see-also"></a>Voir aussi
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
