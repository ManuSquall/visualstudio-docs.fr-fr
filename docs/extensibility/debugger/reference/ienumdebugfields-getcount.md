---
description: Cette méthode retourne le nombre d’éléments dans l’énumération Fields.
title: 'IEnumDebugFields :: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::GetCount
helpviewer_keywords:
- IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a3b2512364ffb8642cb4ebc763d690514ff5fc11
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105052929"
---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
Cette méthode retourne le nombre d’éléments dans l’énumération.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Paramètres
`pcelt`\
à Retourne le nombre d’éléments dans l’énumération.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Cette méthode ne fait pas partie de l’interface d’énumération COM personnalisée qui spécifie que seuls les éléments suivants, de clonage, d’omission et de réinitialisation doivent être implémentés.

## <a name="see-also"></a>Voir aussi
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
