---
title: IDiaSymbol::get_isMultipleInheritance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0aa356a1-5c5c-4ee4-8b48-bae0a2610013
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a353f9fc3605d1f2d26248b3ce907fb76b947c68
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "62836614"
---
# <a name="idiasymbolgetismultipleinheritance"></a>IDiaSymbol::get_isMultipleInheritance
Spécifie si le `this` pointeur pointe vers un membre de données avec l’héritage multiple.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isMultipleInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

[out] Un pointeur vers un `BOOL` qui spécifie si le `this` pointeur pointe vers un membre de données avec l’héritage multiple.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)