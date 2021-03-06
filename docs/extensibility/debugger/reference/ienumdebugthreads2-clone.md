---
description: Retourne une copie de l’énumération des threads en cours sous la forme d’un objet distinct.
title: 'IEnumDebugThreads2 :: Clone | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2::Clone
helpviewer_keywords:
- IEnumDebugThreads2::Clone
ms.assetid: d774322c-e72d-4df3-b317-928da39dadc5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b934bbf6e358296c433a1a59fe675f376d1491ac
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225836"
---
# <a name="ienumdebugthreads2clone"></a>IEnumDebugThreads2::Clone
Retourne une copie de l'énumération actuelle comme un objet distinct.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Clone(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>Paramètres
`ppEnum`\
[out] Retourne une copie de cette énumération en tant qu'objet distinct.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 La copie de l’énumération a le même État que l’original au moment où cette méthode est appelée. Toutefois, le de la copie et les États de l’original sont séparés et peuvent être modifiés individuellement.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
