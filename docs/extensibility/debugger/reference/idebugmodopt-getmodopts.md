---
title: IDebugModOpt::GetModOpts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f5ebced053b80af8dce81d41e6614e89e4ffbf3a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324006"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Récupère une liste des modificateurs facultatifs.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetModOpts(
   ULONG  celt,
   BSTR*  rgelt,
   ULONG* pceltFetched
);
```

```csharp
int GetModOpts(
   uint         celt,
   out string[] rgelt,
   ref uint     pceltFetched
);
```

## <a name="parameters"></a>Paramètres
`celt`\
[in] Nombre d’éléments à retourner.

`rgelt`\
[out] Retourne un tableau qui contient les options.

`pceltFetched`\
[in, out] Nombre d’éléments retournés dans le `rgelt` tableau.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)