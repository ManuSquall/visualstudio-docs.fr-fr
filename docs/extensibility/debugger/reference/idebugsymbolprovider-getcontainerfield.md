---
description: Cette méthode obtient le champ qui contient l’adresse de débogage.
title: 'IDebugSymbolProvider :: GetContainerField | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetContainerField
helpviewer_keywords:
- IDebugSymbolProvider::GetContainerField method
ms.assetid: d6b56b4f-a96b-4fa7-87c1-bac4e58fa766
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c86f3c7ce085b44b3b853736b6fed0f4363e59d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159651"
---
# <a name="idebugsymbolprovidergetcontainerfield"></a>IDebugSymbolProvider::GetContainerField
Cette méthode obtient le champ qui contient l’adresse de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetContainerField( 
   IDebugAddress*         pAddress,
   IDebugContainerField** ppContainerField
);
```

```csharp
int GetContainerField(
   IDebugAddress            pAddress,
   out IDebugContainerField ppContainerField
);
```

## <a name="parameters"></a>Paramètres
`pAddress`\
dans Adresse telle qu’elle est représentée par une interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`ppContainerField`\
à Retourne un champ conteneur représenté par une interface [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) .

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
