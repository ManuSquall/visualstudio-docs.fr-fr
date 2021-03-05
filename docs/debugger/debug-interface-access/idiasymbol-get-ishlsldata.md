---
description: Spécifie si ce symbole représente des données HLSL (High Level Shader Language).
title: IDiaSymbol::get_isHLSLData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4662058b-c505-4ccf-ae03-739a62c814ca
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3850c4b3342d69d214ac9922717e339e8da530e2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160819"
---
# <a name="idiasymbolget_ishlsldata"></a>IDiaSymbol::get_isHLSLData
Spécifie si ce symbole représente des données HLSL (High Level Shader Language).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isHLSLData(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Pointeur vers un `BOOL` qui spécifie si ce symbole représente des données HLSL.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
