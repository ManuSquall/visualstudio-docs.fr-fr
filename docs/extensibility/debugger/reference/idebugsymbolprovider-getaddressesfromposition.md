---
description: Cette méthode mappe une position de document à un tableau d’adresses de débogage.
title: 'IDebugSymbolProvider :: GetAddressesFromPosition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4dd3b8fbe65a72ccf937007d19117359859ff29f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105087104"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Cette méthode mappe une position de document à un tableau d’adresses de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAddressesFromPosition( 
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromPosition( 
   IDebugDocumentPosition2  pDocPos,
   bool                     fStatmentOnly,
   out IEnumDebugAddresses  ppEnumBegAddresses,
   out IEnumDebugAddresses  ppEnumEndAddresses
);
```

## <a name="parameters"></a>Paramètres
`pDocPos`\
dans Position du document.

`fStatmentOnly`\
dans Si la valeur est TRUE, limite les adresses de débogage à une seule instruction.

`ppEnumBegAddresses`\
à Retourne un énumérateur pour les adresses de début de débogage associées à cette instruction ou ligne.

`ppEnumEndAddresses`\
à Retourne un énumérateur [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) pour les adresses de fin de débogage associées à cette instruction ou ligne.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Une position de document indique généralement une plage de lignes sources. Cette méthode fournit les adresses de débogage de début et de fin associées à ces lignes. Certains langages autorisent les instructions qui s’étendent sur plusieurs lignes, ou lignes contenant plusieurs instructions. Cette méthode fournit un indicateur pour limiter les adresses de débogage à une instruction unique.

 Il est possible qu’une seule instruction ait plusieurs adresses de débogage, comme dans le cas de modèles.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
