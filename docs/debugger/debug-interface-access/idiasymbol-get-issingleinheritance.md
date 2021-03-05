---
description: Spécifie si ce pointeur pointe vers un membre de données avec héritage simple.
title: IDiaSymbol::get_isSingleInheritance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 46cde656-059b-4c20-9476-3ca68ccc9912
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 657c677e9415b64f0a42c0ece2ba8847cca9ed51
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160749"
---
# <a name="idiasymbolget_issingleinheritance"></a>IDiaSymbol::get_isSingleInheritance
Spécifie si le `this` pointeur pointe vers un membre de données avec un héritage unique.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isSingleInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Pointeur vers un `BOOL` qui spécifie si le `this` pointeur pointe vers un membre de données avec héritage unique.

## <a name="return-value"></a>Valeur renvoyée
 En cas de réussite, retourne `S_OK` ; sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
