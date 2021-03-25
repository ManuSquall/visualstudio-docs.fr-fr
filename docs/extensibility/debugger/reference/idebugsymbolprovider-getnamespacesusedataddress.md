---
description: Cette méthode crée un énumérateur pour les espaces de noms associés à l’adresse de débogage.
title: 'IDebugSymbolProvider :: GetNamespacesUsedAtAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetNamespacesUsedAtAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetNamespacesUsedAtAddress method
ms.assetid: 392de54b-9af0-4567-953b-1b41acd1e05c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e9f09749cfb3495e71d9cbacfd4a9d430acc107
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087013"
---
# <a name="idebugsymbolprovidergetnamespacesusedataddress"></a>IDebugSymbolProvider::GetNamespacesUsedAtAddress
Cette méthode crée un énumérateur pour les espaces de noms associés à l’adresse de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetNamespacesUsedAtAddress( 
   IDebugAddress*     pAddress,
   IEnumDebugFields** ppEnum
);
```

```csharp
int GetNamespacesUsedAtAddress(
   IDebugAddress        pAddress,
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Paramètres
`pAddress`\
dans Adresse de débogage.

`ppEnum`\
à Retourne un énumérateur [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) pour les espaces de noms.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Il peut y avoir plusieurs espaces de noms associés à une adresse de débogage donnée, par exemple, des espaces de noms imbriqués ou plusieurs `using` instructions.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
