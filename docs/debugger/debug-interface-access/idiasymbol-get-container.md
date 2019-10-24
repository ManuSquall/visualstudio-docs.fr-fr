---
title: IDiaSymbol::get_container | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0533eb2cdea1dd3e1bea3d64e2b94ce29a09353d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740781"
---
# <a name="idiasymbolget_container"></a>IDiaSymbol::get_container
Cette fonction récupère un pointeur vers un symbole représentant le parent/conteneur de ce symbole.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_container(
   IDiaSymbol **pRetVal
);
```

#### <a name="parameters"></a>Paramètres
 `pRetVal`

à Retourne un pointeur vers un `IDiaSymbol` contenant des informations sur le conteneur de ce symbole.

## <a name="return-value"></a>Valeur de retour
 En cas de réussite, retourne S_OK ; Sinon, retourne S_FALSE ou un code d’erreur.

> [!NOTE]
> La valeur de retour S_FALSE signifie que la propriété n’est pas disponible pour le symbole.

## <a name="requirements"></a>spécifications

|Exigence|Description|
|-----------------|-----------------|
|En-tête :|dia2.h|
|Version :|DIA SDK v 8.0|

## <a name="see-also"></a>Voir aussi
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)