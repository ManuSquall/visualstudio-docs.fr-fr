---
title: IDebugSymbolProvider::GetContextFromAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetContextFromAddress
helpviewer_keywords:
- IDebugSymbolProvider::GetContextFromAddress method
ms.assetid: 7a27d56f-20d4-4e5c-af7b-7307d3aff0a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58896285fa0af5eeea972b0c8897472e20c8a128
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347650"
---
# <a name="idebugsymbolprovidergetcontextfromaddress"></a>IDebugSymbolProvider::GetContextFromAddress
Cette méthode mappe une adresse de débogage dans un contexte de document.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetContextFromAddress( 
   IDebugAddress*           pAddress,
   IDebugDocumentContext2** ppDocContext
);
```

```csharp
int GetContextFromAddress(
   IDebugAddress              pAddress,
   out IDebugDocumentContext2 ppDocContext
);
```

## <a name="parameters"></a>Paramètres
`pAddress`\
[in] L’adresse de débogage tel que représenté par un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.

`ppDocContext`\
[out] Retourne un contexte de document, tel que représenté par un [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)