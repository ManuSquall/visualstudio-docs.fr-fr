---
description: Récupère le symbole qui contient l’adresse virtuelle spécifiée.
title: IDiaStackWalkHelper::symbolForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4f75ba05573c5c41baea3ab24ec5b7d06c916c0e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156747"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
Récupère le symbole qui contient l’adresse virtuelle spécifiée.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT symbolForVA( 
   ULONGLONG     va,
   IDiaSymbol**  ppSymbol
);
```

#### <a name="parameters"></a>Paramètres
 `va`

dans Adresse virtuelle contenue dans le symbole demandé. Le symbole doit être un `SymTagFunctionType` (une valeur de l’énumération d' [énumération SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) ).

 `ppSymbol`

à Objet [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) qui représente le symbole à l’adresse spécifiée.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` , sinon, retourne un code d'erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
