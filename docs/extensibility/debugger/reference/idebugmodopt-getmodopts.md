---
description: Récupère une liste de modificateurs facultatifs.
title: 'IDebugModOpt :: GetModOpts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 614ecb456b6f644dfd389020bbffb23691cfbf43
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105081904"
---
# <a name="idebugmodoptgetmodopts"></a>IDebugModOpt::GetModOpts
Récupère une liste de modificateurs facultatifs.

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
dans Nombre d’éléments à retourner.

`rgelt`\
à Retourne un tableau qui contient les options.

`pceltFetched`\
[in, out] Nombre d’éléments retournés dans le `rgelt` tableau.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
