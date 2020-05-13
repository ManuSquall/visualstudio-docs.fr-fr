---
title: IDebugSymbolProviderDirect::GetSymUnmanmanagedReader (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetSymUnmanagedReader
- IDebugSymbolProviderDirect::GetSymUnmanagedReader
ms.assetid: 147bacfa-f66c-43e0-8a72-e601058dc57f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fbac2e234cfc991f27e08dc33bdc895c22d501fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718945"
---
# <a name="idebugsymbolproviderdirectgetsymunmanagedreader"></a>IDebugSymbolProviderDirect::GetSymUnmanagedReader
Récupère un lecteur de symbole pour le code non menté.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSymUnmanagedReader (
   ULONG32    ulAppDomainID,
   GUID       guidModule,
   IUnknown** ppSymUnmanagedReader
);
```

```csharp
int GetSymUnmanagedReader (
   uint       ulAppDomainID,
   Guid       guidModule,
   out object ppSymUnmanagedReader
);
```

## <a name="parameters"></a>Paramètres
`ulAppDomainID`\
[dans] Identification du domaine de l’application.

`guidModule`\
[dans] Identifiant unique du module.

`ppSymUnmanagedReader`\
[out] Retourne un objet qui représente le lecteur de symbole pour le code non menté.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
