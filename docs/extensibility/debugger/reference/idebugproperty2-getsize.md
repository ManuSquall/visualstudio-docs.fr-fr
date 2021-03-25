---
description: Obtient la taille, en octets, de la valeur de la propriété.
title: 'IDebugProperty2 :: obtient | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetSize
helpviewer_keywords:
- IDebugProperty2::GetSize
ms.assetid: 0deb8ec5-d6fb-4622-bb14-0c46b9459cc6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7db319a420dc63eaec8afcdcbeaa38fe861a4bea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064785"
---
# <a name="idebugproperty2getsize"></a>IDebugProperty2::GetSize
Obtient la taille, en octets, de la valeur de la propriété.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSize ( 
   DWORD* pdwSize
);
```

```csharp
int GetSize ( 
   out uint pdwSize
);
```

## <a name="parameters"></a>Paramètres
`pdwSize`\
à Retourne la taille, en octets, de la valeur de la propriété.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne le code d’erreur. Retourne `S_GETSIZE_NO_SIZE` si la propriété n’a pas de taille.

## <a name="see-also"></a>Voir aussi
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
