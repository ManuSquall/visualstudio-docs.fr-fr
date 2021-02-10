---
title: 'IDebugModOpt :: GetModOpts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugModOpt::GetModOpts
- GetModOpts
ms.assetid: cb513fa9-d521-4a65-b968-f55f53a368df
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78ddcaa6a062b844c3f60c04f7a08aa673c69f67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99941786"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)
