---
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
ms.openlocfilehash: a9a7b3f9096bbbef1c4de2161c6bb3b6a4c59e4d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897191"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Remarques
 Un contexte de document indique généralement une plage de lignes sources. Cette méthode fournit les adresses de débogage de début et de fin associées à ces lignes. Certains langages autorisent les instructions qui s’étendent sur plusieurs lignes, ou lignes contenant plusieurs instructions. Cette méthode fournit un indicateur pour limiter les adresses de débogage à une instruction unique.

 Il est possible qu’une seule instruction ait plusieurs adresses de débogage, comme dans le cas de modèles.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
