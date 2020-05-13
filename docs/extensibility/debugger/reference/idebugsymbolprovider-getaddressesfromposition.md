---
title: IDebugSymbolProvider::GetAddressesDePosition (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27767af36093e9424775074a55bafadac9a4480d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719408"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
Cette méthode cartographie la position d’un document dans un tableau d’adresses de débogé.

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
[dans] La position du document.

`fStatmentOnly`\
[dans] Si VRAI, limite les adresses de débogé à une seule instruction.

`ppEnumBegAddresses`\
[out] Retourne un enumérateur pour les adresses de débaçon de départ associées à cette déclaration ou ligne.

`ppEnumEndAddresses`\
[out] Retourne un enumérateur [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) pour les adresses de débaillement de fin associées à cette déclaration ou ligne.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="remarks"></a>Notes
 Une position de document indique généralement une gamme de lignes sources. Cette méthode fournit les adresses de débaillement de démarrage et de fin associées à ces lignes. Certaines langues permettent des déclarations qui s’étendent sur plusieurs lignes, ou des lignes qui contiennent plus d’une instruction. Cette méthode fournit un drapeau pour limiter les adresses de débogé à une seule instruction.

 Il est possible pour une seule déclaration d’avoir plusieurs adresses de débogé, comme dans le cas des modèles.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
