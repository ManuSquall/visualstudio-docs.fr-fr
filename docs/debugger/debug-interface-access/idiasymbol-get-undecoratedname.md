---
title: IDiaSymbol::get_undecoratedName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedName method
ms.assetid: e49edf25-a51d-4787-bd5b-2bf5af827c8c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 533fc28da8cdd500234e07d2294a9d503476568e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72739013"
---
# <a name="idiasymbolget_undecoratedname"></a>IDiaSymbol::get_undecoratedName
Récupère le nom non décoré pour un C++ nom décoré ou de liaison.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_undecoratedName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne le nom non décoré pour un C++ nom décoré.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne `S_OK` ; Sinon, retourne `S_FALSE` ou un code d’erreur.

> [!NOTE]
> Une valeur de retour de `S_FALSE` signifie que la propriété n’est pas disponible pour le symbole.

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)