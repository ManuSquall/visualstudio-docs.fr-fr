---
description: Récupère le nombre d’index de registre.
title: IDiaSymbol::get_numberOfRegisterIndices | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 1ec8b8ea-e423-4327-8dc0-a390e6e3ffb0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fc328522a0c4d998642c4f58fd5409daeccac742
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160735"
---
# <a name="idiasymbolget_numberofregisterindices"></a>IDiaSymbol::get_numberOfRegisterIndices
Récupère le nombre d’index de registre.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_numberOfRegisterIndices(
   DWORD* pRetVal);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Pointeur vers un `DWORD` qui contient le nombre d’index de registre.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
