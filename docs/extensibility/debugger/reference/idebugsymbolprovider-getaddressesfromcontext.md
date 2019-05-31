---
title: IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ff38d2bd286c0a1ff82aafc3526936447be69056
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335216"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
Cette méthode mappe un contexte de document dans un tableau d’adresses de débogage.

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
[in] Le contexte du document.

`fStatmentOnly`\
[in] Si la valeur est TRUE, limite les adresses de débogage à une seule instruction.

`ppEnumBegAddresses`\
[out] Retourne un énumérateur pour les adresses de débogage début associé à cette instruction ou de la ligne.

`ppEnumEndAddresses`\
[out] Retourne un [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) énumérateur pour les adresses de débogage fin associée à cette instruction ou de la ligne.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="remarks"></a>Notes
 Un contexte de document indique généralement une plage de lignes sources. Cette méthode fournit le début et fin des adresses de débogage associés à ces lignes. Certains langages permettent aux instructions qui s’étendent sur plusieurs lignes, ou qui contient plusieurs instructions. Cette méthode fournit un indicateur pour limiter les adresses de débogage à une seule instruction.

 Il est possible qu’une seule instruction d’avoir plusieurs adresses de débogage, comme dans le cas des modèles.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)