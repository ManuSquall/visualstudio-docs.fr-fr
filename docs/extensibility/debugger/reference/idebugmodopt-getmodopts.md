---
title: IDebugModOpt::GetModOpts ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5ab870db3ae3517b60bebd4815e4530f6035b327
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727050"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Récupère une liste de modificateurs optionnels.

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
[dans] Nombre d’éléments à retourner.

`rgelt`\
[out] Retourne un tableau qui contient les options.

`pceltFetched`\
[dans, dehors] Nombre d’éléments `rgelt` retournés dans le tableau.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
