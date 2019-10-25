---
title: IDiaStackWalkHelper::symbolForVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f646616fddc0e7727ef9e8e80d9c29fbcba6ebc0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741321"
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

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)