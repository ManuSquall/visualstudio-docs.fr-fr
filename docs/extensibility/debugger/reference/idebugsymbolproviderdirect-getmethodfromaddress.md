---
title: 'IDebugSymbolProviderDirect :: GetMethodFromAddress | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetMethodFromAddress
- GetMethodFromAddress
ms.assetid: 33ffd197-1221-41bc-a9f6-f133ebdcb783
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3cbcab2126ffa61f4bfb71fbf21abff8ecc5d798
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909439"
---
# <a name="idebugsymbolproviderdirectgetmethodfromaddress"></a>IDebugSymbolProviderDirect::GetMethodFromAddress
Récupère des informations sur la méthode à l’adresse de débogage spécifiée.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMethodFromAddress(
   IDebugAddress* pAddress,
   GUID*          pGuid,
   DWORD*         pAppID,
   _mdToken*      pTokenClass,
   _mdToken*      pTokenMethod,
   DWORD*         pdwOffset,
   DWORD*         pdwVersion
);
```

```csharp
int GetMethodFromAddress(
   IDebugAddress pAddress,
   out Guid      pGuid,
   out uint      pAppID,
   out uint      pTokenClass,
   out uint      pTokenMethod,
   out uint      pdwOffset,
   out uint      pdwVersion
);
```

## <a name="parameters"></a>Paramètres
`pAddress`\
dans Adresse de débogage qui est représentée par l’interface [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .

`pGuid`\
à Identificateur unique du module.

`pAppID`\
à Identificateur du domaine d’application.

`pTokenClass`\
à Jeton qui représente la classe conteneur.

`pTokenMethod`\
à Jeton qui représente le module.

`pdwOffset`\
à Offset, en octets, à partir du début du `pAddress` paramètre.

`pdwVersion`\
à Numéro de version de la méthode.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
