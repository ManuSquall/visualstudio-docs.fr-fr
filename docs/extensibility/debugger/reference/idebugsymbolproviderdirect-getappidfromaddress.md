---
title: IDebugSymbolProviderDirect::GetAppIDFromAddress | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSymbolProviderDirect::GetAppIDFromAddress
- GetAppIDFromAddress
ms.assetid: d76a0f36-79c4-4c58-9db3-880b00d11610
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c0c2781038eae4f1a896b8d6627edb2969e35ff
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713800"
---
# <a name="idebugsymbolproviderdirectgetappidfromaddress"></a>IDebugSymbolProviderDirect::GetAppIDFromAddress
Récupère l’identificateur de domaine d’application étant donné l’adresse de débogage.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetAppIDFromAddress(
   IDebugAddress* pAddress,
   DWORD*         pAppID
);
```

```csharp
int GetAppIDFromAddress(
   IDebugAddress pAddress,
   out uint      pAppID
);
```

#### <a name="parameters"></a>Paramètres
 `pAddress`

 [in] Déboguer l’adresse qui est représenté par le [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) interface.

 `pAppID`

 [out] Identificateur du domaine d’application.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)