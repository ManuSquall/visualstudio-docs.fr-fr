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
ms.openlocfilehash: 4eb6e1509a46c4e584e98403439188581df97c10
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740178"
---
# <a name="idiasymbolget_ismultipleinheritance"></a>IDiaSymbol::get_isMultipleInheritance
Spécifie si le pointeur de `this` pointe vers un membre de données avec héritage multiple.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_isMultipleInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Pointeur vers un `BOOL` qui spécifie si le pointeur de `this` pointe vers un membre de données avec héritage multiple.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)