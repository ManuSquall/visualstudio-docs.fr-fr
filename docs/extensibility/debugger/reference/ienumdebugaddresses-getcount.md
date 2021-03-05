---
description: Cette méthode retourne le nombre d’éléments dans l’énumération Addresses.
title: 'IEnumDebugAddresses :: GetCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::GetCount
helpviewer_keywords:
- IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 092cba3ce0def2f416a4676e86df89bd56fd87e4
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222677"
---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
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
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
