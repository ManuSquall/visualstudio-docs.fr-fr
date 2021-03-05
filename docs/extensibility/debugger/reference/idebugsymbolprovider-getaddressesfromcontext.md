---
description: Cette méthode mappe un contexte de document à un tableau d’adresses de débogage.
title: 'IDebugSymbolProvider :: GetAddressesFromContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7fcbc974fe3556f16d339f8be8b8f1738fa8eb74
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159690"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Cette méthode mappe un contexte de document à un tableau d’adresses de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAddressesFromContext( 
   IDebugDocumentContext2* pDocContext,
   BOOL                    fStatmentOnly,
   IEnumDebugAddresses**   ppEnumBegAddresses,
   IEnumDebugAddresses**   ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromContext(
   IDebugDocumentContext2  pDocContext,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>Paramètres
`pDocContext`\
dans Contexte du document.

`fStatmentOnly`\
dans Si la valeur est TRUE, limite les adresses de débogage à une seule instruction.

`ppEnumBegAddresses`\
à Retourne un énumérateur pour les adresses de début de débogage associées à cette instruction ou ligne.

`ppEnumEndAddresses`\
à Retourne un énumérateur [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) pour les adresses de fin de débogage associées à cette instruction ou ligne.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Un contexte de document indique généralement une plage de lignes sources. Cette méthode fournit les adresses de débogage de début et de fin associées à ces lignes. Certains langages autorisent les instructions qui s’étendent sur plusieurs lignes, ou lignes contenant plusieurs instructions. Cette méthode fournit un indicateur pour limiter les adresses de débogage à une instruction unique.

 Il est possible qu’une seule instruction ait plusieurs adresses de débogage, comme dans le cas de modèles.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
