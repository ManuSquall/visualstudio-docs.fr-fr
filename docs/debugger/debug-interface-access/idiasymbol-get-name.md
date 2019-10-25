---
title: IDiaSymbol::get_name | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_name method
ms.assetid: 050ec02f-b7b3-48fc-8e35-58bdf7d938b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 754416049197a92344fd238b28ec99e8fb912791
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739763"
---
# <a name="idiasymbolget_name"></a>IDiaSymbol::get_name
Récupère le nom du symbole.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_name ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le nom du symbole.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="example"></a>Exemple

```C++
IDiaSymbol* pType;
BSTR        name;
pType->get_name( &name );
```

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)